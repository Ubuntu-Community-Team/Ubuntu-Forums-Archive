---
title: "What to do with a PKGBUILD file ?"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by raveeshpr on 2007-09-30
Hi frnds

i am a newbe in linux and started using for only 3 days. 

while searching for Bluesnarfer in net, i got a file named PKGBUILD. 
with the content like

# Contributor: DigitalPathogen <aur@isrlabs.com>

pkgname=bluesnarfer
pkgver=0.1
pkgrel=3
pkgdesc="A bluetooth snarfing tool"
url="http://www.alighieri.org"
depends=('bluez-libs')
source=(http://www.alighieri.org/tools/$pkgname.tar.gz)
md5sums=('ee1fcf2e12b74e8cf65f43cdd2c47b72')

build() {
  cd $startdir/src/$pkgname
  make || return 1
  install -m 0755 -d $startdir/pkg/usr/bin
  install -m 0755 $startdir/src/$pkgname/$pkgname $startdir/pkg/usr/bin
}

can anybody help me what to do with this file to install bluesnarfer.

Tnaks in advance. 

Raveesh

---

