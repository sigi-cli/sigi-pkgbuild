# Maintainer: J.R. Hill <justin@so.dang.cool>
pkgname="sigi"
pkgver="3.6.4"
pkgrel=1
pkgdesc="Organization CLI for people who hate organization"
arch=('x86_64' 'aarch54')
url="https://github.com/sigi-cli/sigi"
license=('GPL-2.0-only')
makedepends=('cargo')
source=("$pkgname-$pkgver.tar.gz::https://crates.io/api/v1/crates/sigi/$pkgver/download")
sha256sums=('3bccc00077f7fc746c19df643ca9f1b3dbb06de4132ee60c96dc26370e97eaf6')

build() {
	cd "$pkgname-$pkgver"

	cargo build --release --locked
}

check() {
	cd "$pkgname-$pkgver"

	# Tests are skipped until https;//github.com/hiljusti/sigi/issues/19
	SKIP_BATS_TESTS=1 cargo test --release --locked
}

package() {
	cd "$pkgname-$pkgver"

	install -Dm755 "target/release/sigi" "$pkgdir/usr/bin/sigi"

	install -Dm644 "sigi.1" "$pkgdir/usr/share/man/man1/sigi.1"
}

