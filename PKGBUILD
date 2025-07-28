# Maintainer: Leandro Guedes <leanguedes at icloud dot com>

pkgname=keepsecret-git
pkgver=r165.c68b694
pkgrel=1
pkgdesc='Password manager for viewing, editing, creating, or deleting passwords'
arch=('x86_64')
url='https://invent.kde.org/mart/keepsecret'
license=('GPL-2.0-or-later')
depends=(
  gcc-libs
  glib2
  glibc
  kcolorscheme
  kconfig
  kcoreaddons
  kcrash
  kdbusaddons
  ki18n
  kiconthemes
  kirigami
  kirigami-addons
  kitemmodels
  libsecret
  qqc2-desktop-style
  qt6-base
  qt6-declarative
  qt6-svg
)
makedepends=(
  extra-cmake-modules
  git
  qt6-tools
  vulkan-headers
)
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=("${pkgname%-git}::git+https://invent.kde.org/mart/keepsecret.git")
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/${pkgname%-git}"

  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S "${pkgname%-git}" \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
