# Contributer: James Pearson <james.m.pearson+arch@gmail.com>
# Previous Contributor: Xilon <xilonmu@gmail.com>

# gtkmm is not needed if you remove --enable-gui
# curl is not needed if you remove --enable-url, which allows loading a torrent directly from the web

pkgname='btg'
pkgver='0.9.9'
pkgrel=5
pkgdesc='Linux bittorrent client implemented in C++ and using the rasterbar libtorrent library.'
url='http://btg.berlios.de/'
arch=('i686' 'x86_64')
license=('GPL')
depends=('libtorrent-rasterbar>=0.12' 'gnutls' 'dialog' 'gtkmm>=2.6.0' 'curl>=7.15.5')
options=('!libtool' '!emptydirs' 'force')
source=("http://download2.berlios.de/${pkgname}/${pkgname}-${pkgver}.tar.gz")
install=${pkgname}.install

build() {
  cd "${startdir}/src/${pkgname}-${pkgver}"
  patch -p0 < ../../no_wide_char_check.patch || return 1
  ./configure --prefix=/usr \
    --enable-btg-config \
    --enable-session-saving \
    --enable-cli \
    --enable-gui \
    --enable-www \
    --enable-url \
    --with-boost-date-time=mt \
    --with-boost-filesystem=mt \
    --with-boost-thread=mt \
    --with-boost-regex=mt \
    --with-boost-program-options=mt || return 1

  make || return 1
  make DESTDIR=$startdir/pkg install || return 1
}
md5sums=('1224192af53d7ddf2dd86c2e61027db6')
