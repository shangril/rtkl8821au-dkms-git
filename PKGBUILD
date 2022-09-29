# Maintainer : Shangri-l <nico (at)nicolaschartoire(dot)com>
# Prefork x86 Maintainer: zebulon <zeb (at)zebulon(dot)org(dot)uk>
# Contributor: NovaMoon <novamoon1 (at)gmail(dot)com> for the git that was forked

pkgname=rtkl8821au-dkms-git
_pkgbase=rtkl8821au
pkgver=5.12.5.2.r174.g9c682a9
pkgrel=1
pkgdesc="aarch64-enabled for sunxi platform (mainly, read Pine64 : A64-lts and SoPine baseboard) rtl8821AU and rtl8811AU chipset driver with firmware v5.12.5.2"
arch=('aarch64')
url="https://github.com/shangril/rtkl8821au-20210708"
license=('GPL2')
depends=('dkms' 'bc')
makedepends=('git')
conflicts=("${_pkgbase}" '8821au')
source=("git+https://github.com/shangril/rtkl8821au-20210708.git"
        'dkms.conf')
sha256sums=('SKIP'
	    '4c1278e03939298a8bcabfbe63bd995417363601e09583c1125c31df375834f6')
            

pkgver() {
    cd ${srcdir}/rtkl8821au-20210708
    printf '%s.r%s.g%s' '5.12.5.2' "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
        cd ${srcdir}/rtkl8821au-20210708
        mkdir -p ${pkgdir}/usr/src/${_pkgbase}-${pkgver}
        cp -pr * ${pkgdir}/usr/src/${_pkgbase}-${pkgver}
        cp ${srcdir}/dkms.conf ${pkgdir}/usr/src/${_pkgbase}-${pkgver}
        # Set name and version
        sed -e "s/@_PKGBASE@/${_pkgbase}-dkms/" \
                        -e "s/@PKGVER@/${pkgver}/" \
                        -i "${pkgdir}"/usr/src/${_pkgbase}-${pkgver}/dkms.conf
}
