---
title: "Issues with ugrading from 7.04 to 7.1, unable to find...things?"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by snwbord2456 on 2007-11-03
When trying to upgrade from 7.04 to 7.1 I get the following error message when the upgrade tool is downloading the necessary packages (right term?). The error is:

Failed to fetch [http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch 
[http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2](http://download.tuxfamily.org/3v1deb/dists/feisty/eyecandy/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 404 Not Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 404 Not Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 404 Not Found

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 404 Not Found

---

### Post by linuxwizard on 2007-11-03
Try removing or disable any extra repos you add to your source list. The medibuntu repo can be removed after upgrading you can add them back when done for Gusty .

---

