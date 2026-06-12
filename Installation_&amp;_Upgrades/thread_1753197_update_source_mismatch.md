---
title: "update source mismatch?"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by nandinga on 2011-05-08
Hi!

Update manager is showing me an update for libraw1394-11 from a users PPA instead of from the Ubuntu repos.

If I'm not understanding it wrong, that package comes from Ubuntu's main repo. See the result of apt-cache show below.

But I've installed a PPA for the CPU frequency indicator, and Update Manager says that the update comes from there.

Why is this happening? Am I not understanding something?

BTW I'm running Natty.

Thx!!

```
$ apt-cache show libraw1394-11 
Package: libraw1394-11
Priority: optional
Section: libs
Installed-Size: 136
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Guus Sliepen <guus@debian.org>
Architecture: i386
Source: libraw1394
Version: 2.0.6-1
Depends: libc6 (>= 2.4)
Suggests: libraw1394-doc
Filename: pool/main/libr/libraw1394/libraw1394-11_2.0.6-1_i386.deb
Size: 31892
MD5sum: e6589eefaf5637c703fe131564e29854
SHA1: bf1ac877c5672dcbc26311a08d595bbca5f528e5
SHA256: 8c0997786f01ad419886039f0f4164a3440dafe19335d41b08ac02f1b8bb7625
Description: library for direct access to IEEE 1394 bus (aka FireWire)
 libraw1394 is the only supported interface to the kernel side raw1394
 of the Linux IEEE-1394 subsystem, which provides direct access to the
 connected 1394 buses to user space.  Through libraw1394/raw1394,
 applications can directly send to and receive from other nodes without
 requiring a kernel driver for the protocol in question.
Homepage: https://ieee1394.wiki.kernel.org/
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m
Task: ubuntu-desktop, ubuntu-uec-live, kubuntu-desktop, kubuntu-mobile-desktop, kubuntu-mobile, edubuntu-desktop, edubuntu-desktop-kde, edubuntu-uec-live, xubuntu-desktop, mythbuntu-backend-master, mythbuntu-backend-master, mythbuntu-backend-slave, mythbuntu-backend-slave, mythbuntu-desktop, mythbuntu-frontend, mythbuntu-frontend, ubuntu-netbook

Package: libraw1394-11
Source: libraw1394
Priority: optional
Section: libs
Installed-Size: 136
Maintainer: Guus Sliepen <guus@debian.org>
Architecture: i386
Version: 2.0.7-1~natty1
Suggests: libraw1394-doc
Depends: libc6 (>= 2.4)
Filename: pool/main/libr/libraw1394/libraw1394-11_2.0.7-1~natty1_i386.deb
Size: 46320
MD5sum: f37e812bcba389752fa53c1873cabe21
SHA1: 87ecb154c4b67fe82103f5277a2e453cf23caab7
Description: library for direct access to IEEE 1394 bus (aka FireWire)
 libraw1394 is the only supported interface to the kernel side raw1394
 of the Linux IEEE-1394 subsystem, which provides direct access to the
 connected 1394 buses to user space.  Through libraw1394/raw1394,
 applications can directly send to and receive from other nodes without
 requiring a kernel driver for the protocol in question.

```

---

### Post by zvacet on 2011-05-08
It is same package,but one you get from PPA is higher version theen one you get from Ubuntu repos.


> apt-cache show libraw1394-11 
Package: libraw1394-11
Priority: optional
Section: libs
Installed-Size: 136
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Guus Sliepen <guus@debian.org>
Architecture: i386
Source: libraw1394
**Version: 2.0.6-1**

and from PPA

> Package: libraw1394-11
Source: libraw1394
Priority: optional
Section: libs
Installed-Size: 136
Maintainer: Guus Sliepen <guus@debian.org>
Architecture: i386
**Version: 2.0.7-1**~natty1

---

