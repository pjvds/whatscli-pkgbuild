# Maintainer: Pieter Joost van de Sande <pj@born2code.net>
pkgname=whatscli
pkgver=1.0.8
pkgrel=1
pkgdesc='A command line interface for whatsapp, based on go-whatsapp and tview'
arch=('1686' 'x86_64' 'armv7h' 'armv6h' 'aarch64')
url='https://github.com/normen/whatscli'
makedepends=('go' 'git')
source=("${pkgname}-${pkgver}.tar.gz::https://github.com/normen/whatscli/archive/v${pkgver}.tar.gz")
sha1sums=('533148e747a424c9bc598d1b604bb86c94e744bc')

build() {
    cd "${pkgname}-${pkgver}"
    export CGO_CPPFLAGS="${CPPFLAGS}"
    export CGO_CFLAGS="${CFLAGS}"
    export CGO_CXXFLAGS="${CXXFLAGS}"
    export GOFLAGS="-buildmode=pie -trimpath -mod=readonly -modcacherw"
    go build -o ${pkgname} -ldflags "-extldflags ${LDFLAGS} -s -w -X main.version=${pkgver}" main.go
}

package() {
    install -Dm755 "${pkgname}-${pkgver}/${pkgname}" ${pkgdir}/usr/bin/${pkgname}
}
