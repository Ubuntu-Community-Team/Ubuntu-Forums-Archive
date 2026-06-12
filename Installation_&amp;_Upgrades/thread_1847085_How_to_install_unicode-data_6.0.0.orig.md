---
title: "How to install unicode-data_6.0.0.orig"
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by ernsttremel on 2011-09-20
I got unicode-data_6.0.0.orig.tar.gz 
containing
UCD.zip
and
Unihan.zip.

My question is
are these Files already installed in Ubuntu 11.04.

If not what hw to proceed to getting them installed?

[http://ftp.at.debian.org/debian/pool/main/u/unicode-data/unicode-data_6.0.0-1.dsc](http://ftp.at.debian.org/debian/pool/main/u/unicode-data/unicode-data_6.0.0-1.dsc)

---

### Post by mikewhatever on 2011-09-20
No, unicode and unicode-data are not pre-installed. If you need them, use the Software Center. Installing Debian packages in Ubuntu would probably fail or break something.

---

### Post by ernsttremel on 2011-09-21
> **mikewhatever said:**
> No, unicode and unicode-data are not pre-installed. If you need them, use the Software Center. Installing Debian packages in Ubuntu would probably fail or break something.

But 
unicode 
and
unicode-data 
are not to be found in the Software Center of Ubuntu 11.04

---

### Post by mikewhatever on 2011-09-21
I am pretty sure they are there, unless your sources list is messed up. Let's see the output of the following:
```
apt-cache show unicode unicode-data
```

---

### Post by ernsttremel on 2011-09-22
apt-cache show unicode unicode-data
Package: unicode
Priority: optional
Section: universe/utils
Installed-Size: 96
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Radovan Garabík <garabik@kassiopeia.juls.savba.sk>
Architecture: all
Version: 0.9.5
Depends: python (>= 2.3)
Suggests: perl-modules | console-data (<< 2:1.0-1) | unicode-data
Filename: pool/universe/u/unicode/unicode_0.9.5_all.deb
Size: 14796
MD5sum: 52c08d0048f6ef542653fd4e0cc5100c
SHA1: 89395795436f55a9edbc7a305107b2da10c64c69
SHA256: 058476bc6dbe2c591110f5692dd58cfdd9340ed4becb23c79b51e6420f606ba7
Description: display unicode character properties
 unicode is a simple command line utility that displays
 properties for a given unicode character, or searches
 unicode database for a given name.
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

[SIZE=4][COLOR=Red]Package: unicode-data[/COLOR][/SIZE]
Priority: optional
Section: universe/misc
Installed-Size: 17924
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Alastair McKinstry <mckinstry@debian.org>
Architecture: all
[SIZE=4][COLOR=Red]Version: 6.0.0[/COLOR][/SIZE][SIZE=4]-1[/SIZE]
Filename: pool/universe/u/unicode-data/unicode-data_6.0.0-1_all.deb
Size: 7121942
MD5sum: b59faff9341d8e5235d786f1d46e8741
SHA1: 1630ab32299c0be4f9964987203856392f56895f
SHA256: adee57126f7be24a4e00b0cf446b069d9219acaf9b5297bc77a6041d5467f45e
Description: Property data for the Unicode character set
 This package contains the property data, for the Unicode data set.
Homepage: [http://www.unicode.org/](http://www.unicode.org/)
Bugs: [https://bugs.launchpad.net/ubuntu/+filebug](https://bugs.launchpad.net/ubuntu/+filebug)
Origin: Ubuntu

Although there is "unicode-data" version 6.0.0 in Ubuntu 11.04 installed, the display is not correct.
cf
HindiFont-BabelMap-WindowsXP-Unicode 6.0.0.JPG
and
HindiFont-Ubuntu11.04-Unicode 6.0.0.png

---

