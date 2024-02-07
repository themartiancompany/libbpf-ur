# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer:  Pellegrino Prevete <cGVsbGVncmlub3ByZXZldGVAZ21haWwuY29tCg== | base -d>
# Maintainer:  Truocolo <truocolo@aol.com>
# Maintainer:  Adrian Bacircea <adrian.bacircea@gmail.com>

pkgname=libbpf
pkgver=0.0.7
pkgrel=1
pkgdesc='BPF library'
depends=(
  'libelf'
  'linux-api-headers'
)
url='https://github.com/libbpf/libbpf'
license=(
  'custom'
)
makedepends=(
  'rsync'
)
arch=(
  'x86_64'
  'arm'
)
source=(
  "git+https://github.com/libbpf/libbpf#tag=v${pkgver}"
  "check-reallocarray.sh"
)
sha256sums=(
  'SKIP'
  'ef627f22f16df9fc3694a5155fff4ba7820529c8661c8ccac0b3b62dd4d2046c'
)

prepare () {
  cp \
    "check-reallocarray.sh" \
    "${srcdir}/${pkgname}/scripts"
  cd \
    "${srcdir}/${pkgname}"
}

build() {
  cd \
    "${srcdir}/${pkgname}/src"
  cat \
    Makefile
  make
}

package() {
  cd \
    "${srcdir}/${pkgname}/src"
  DESTDIR="${pkgdir}" \
    make \
      prefix=/usr \
      install \
      install_headers
  install \
    -d \
    "${pkgdir}/usr/share/licenses/${pkgname}"
  install \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}" \
    "${srcdir}/${pkgname}/LICENSE"
  install \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}" \
    "${srcdir}/${pkgname}/LICENSE.BSD-2-Clause"
  pushd \
    "${pkgdir}/usr"
  [[ -e lib64 ]] && \
    mv \
      lib64 \
      lib
  popd
}

# vim:set sw=2 sts=-1 et:
