---
title: "When I rebuild package it show this message, what should I do?"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by wuddy on 2007-10-04
I try to rebuild package for aircrack-ng and I got a problem here
I start with this

apt-get install build-essential devscripts dpkg-dev debhelper
wget [http://ftp.debian.org/debian/pool/main/a/aircrack-ng/aircrack-ng_0.9.1-1.dsc](http://ftp.debian.org/debian/pool/main/a/aircrack-ng/aircrack-ng_0.9.1-1.dsc)
wget [http://ftp.debian.org/debian/pool/main/a/aircrack-ng/aircrack-ng_0.9.1-1.diff.gz](http://ftp.debian.org/debian/pool/main/a/aircrack-ng/aircrack-ng_0.9.1-1.diff.gz)
wget [http://ftp.debian.org/debian/pool/main/a/aircrack-ng/aircrack-ng_0.9.1.orig.tar.gz](http://ftp.debian.org/debian/pool/main/a/aircrack-ng/aircrack-ng_0.9.1.orig.tar.gz)
dpkg-source -x aircrack-ng_0.9.1-1.dsc
cd aircrack-ng_0.9.1

Next I will rebuild the package


root@Eubuntu:/home/wudiwudy/Aircrack-0.9.1/aircrack-ng-0.9.1-ubuntu6.06/aircrack-ng-0.9.1# dpkg-buildpackage
dpkg-buildpackage: source package is aircrack-ng
dpkg-buildpackage: source version is 1:0.9.1-1
dpkg-buildpackage: source changed by Adam Cécile (Le_Vert) <gandalf@le-vert.net>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: dpatch
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

Something wrong with it, I don't know
I try again with -d and it shows

root@Eubuntu:/home/wudiwudy/Aircrack-0.9.1/aircrack-ng-0.9.1-ubuntu6.06/aircrack-ng-0.9.1# dpkg-buildpackage -d
dpkg-buildpackage: source package is aircrack-ng
dpkg-buildpackage: source version is 1:0.9.1-1
dpkg-buildpackage: source changed by Adam Cécile (Le_Vert) <gandalf@le-vert.net>
dpkg-buildpackage: host architecture i386
 debian/rules clean
debian/rules:7: /usr/share/dpatch/dpatch.make: No such file or directory
make: *** No rule to make target `/usr/share/dpatch/dpatch.make'.  Stop.


What should I do???? please help me

Thank you in advance

---

