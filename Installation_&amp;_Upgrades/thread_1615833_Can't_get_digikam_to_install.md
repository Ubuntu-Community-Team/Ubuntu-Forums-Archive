---
title: "Can't get digikam to install"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by nymusicman on 2010-11-07
Admittedly, I installed the PinguyOS version of Maverick, but even after disabling all the repositories that came with it I still couldn't get this to work. Therefore this must be a problem with Ubuntu 10.10 itself, however if this problem does exist is Ubuntu, I'm surprised these forums are flooded with complaints. I've searched them up and down and I found nothing.

Anyway, the problem is that I can't install digikam, this is the error I get:

The following packages have unmet dependencies.
 digikam : Depends: kdebase-runtime but it is not going to be installed
           Depends: kdepim-runtime but it is not going to be installed
           Depends: libkde3support4 (>= 4:4.4.4) but it is not going to be installed
           Depends: libqt4-qt3support (>= 4:4.5.3) but it is not going to be installed
           Recommends: kipi-plugins but it is not going to be installed
E: Broken packages


The problem here seems to be that the kde libraries that come with ubuntu are version 4.5 for everything. And it seems digikam 1.4 is built against kde 4.4.

Has anyone else experienced this problem. Please help!!!

---

### Post by nymusicman on 2010-11-08
I have fixed this problem for myself and am posting the answer here as well as over at the forums of PinguyOS.

I downloaded and installed the following from packages.ubuntu.com (maverick section):

libqt4-dbus
libqtcore4
libqt4-xml
libqtcore4
libqt4-network
libqt4-opengl
libqt4-sql
libqt4-sql-mysql
libqt4-sql-sqlite
libqt4-svg
libqtgui4

To install just download all these files in a directory and "sudo dpkg -i install *.deb"

From here I "sudo apt-get install libqt4-script"
When this app installed correctly "sudo apt-get install digikam" succeeded.

Thanks.

---

