_modname=nvidia_bl
_oldpkgver=0.17.3
pkgname=nvidia-bl-dkms
pkgver=0.17.3
pkgrel=1
pkgdesc="Driver to adjust display backlight on modern mobile NVidia graphics adapters. This version has to be used in conjunction with DKMS."
arch=('i686' 'x86_64')
license=('GPL')
depends=('dkms' 'linux')
makedepends=('linux-headers')
conflicts=('nvidia-bl')
install=nvidia-bl-dkms.install

source=('nvidia-bl-dkms-0.17.3.tar.gz')
md5sums=('a2b34411bb6a2954c09242de3102dcb9')

build() {
  tar zxvf nvidia-bl-dkms-0.17.3.tar.gz
}

package() {
  mkdir -p $pkgdir/usr/src/${_modname}-$pkgver
  cp -a $srcdir/nvidia-bl-dkms-${pkgver}/usr/src/dkms_source_tree/* \
 	$pkgdir/usr/src/${_modname}-$pkgver
  install -d -m755 $pkgdir/etc/modprobe.d
  echo "blacklist mbp_nvidia_bl" >> $pkgdir/etc/modprobe.d/nvidia-bl-dkms.conf
  sed -i -e "s/OLD_PACKAGE_VERSION/${_oldpkgver}/" $startdir/nvidia-bl-dkms.install
  sed -i -e "s/PACKAGE_VERSION/${pkgver}/" $startdir/nvidia-bl-dkms.install
}
