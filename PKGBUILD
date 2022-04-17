pkgname=i3-tools
pkgver=0.2.1
pkgrel=1
pkgdesc="Tools for the i3 window manager"
arch=('x86_64')
license=('MIT')
url="https://github.com/vincentsavard/i3-tools"
makedepends=(cargo)
source=("git+https://github.com/vincentsavard/i3-tools.git")
sha512sums=('SKIP')

prepare() {
    cd $pkgname
    cargo fetch --locked --target "$CARCH-unknown-linux-gnu"
}

build() {
    export RUSTUP_TOOLCHAIN=stable
    export CARGO_TARGET_DIR=target
    cd $pkgname
    cargo build --frozen --release --all-features
}

check() {
    export RUSTUP_TOOLCHAIN=stable
    cd $pkgname
    cargo test --frozen --all-features
}

package() {
    cd $pkgname
    install -Dm0755 -t "$pkgdir/usr/bin/" "target/release/$pkgname"
}
