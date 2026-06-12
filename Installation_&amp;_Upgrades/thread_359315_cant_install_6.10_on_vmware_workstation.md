---
title: "cant install 6.10 on vmware workstation"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by dav2900 on 2007-02-11
I'm running WinXP Pro with VMWare 5.5.3 workstation.  I downloaded the 6.10 Ubuntu ISO (ubuntu-6.10-desktop-i386.iso) and burned it to CD.  I configured the new vmware session following some docs I found online: Linux 2.6.x kernel, 512 Mb RAM, 4 Gb preallocated partition.  If I start the machine with Ubuntu CD loaded, it boots off the CD (no option to install).  If I adjust the vmware image setting for CD-Rom to use the ISO image from my hard drive, it does the same (but loads it much faster than off the CD).  It never asks me to 'install' it (even though the boot menu option says boot/install).  Instead, it just boots off the CDROM or ISO image.
I'm a VMware and Ubuntu newbie.  Thanks for any help!

---

### Post by wickstopher on 2007-02-11
The LiveCD should boot into a working version of Ubuntu, selecting the boot/install option.  From there, there will be an icon on the desktop labelled "Install."  That should do the trick.

---

### Post by dav2900 on 2007-02-11
D'oh!! That did it.  Thanks.

---

