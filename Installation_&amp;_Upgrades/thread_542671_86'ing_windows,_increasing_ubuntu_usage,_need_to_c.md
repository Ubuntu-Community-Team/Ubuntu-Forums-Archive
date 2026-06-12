---
title: "86'ing windows, increasing ubuntu usage, need to change install"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by svtfmook on 2007-09-04
my current setup:
3 x 250GB HDD's (2 x 250 RAID0 windows, 1 w/ 100GB partition for ubuntu and ~100GB for windows backup files)

what i want to do increase the ubuntu partition to use the entire drive, use one of the other 250GB drives for backup for ubuntu and the 3rd 250GB drive to run windows just for gaming.

what would be the best way to do this without losing my ubuntu installation or setup?

do i just run gparted and increase the partition size?

---

### Post by tgalati4 on 2007-09-04
Well, 100 GB is HUGE for an Ubuntu installation.  You can simply wipe and reformat the windows partitions using cfdisk or gparted.  If they are going to be just for data storage, they you can probably get away with ext2 format.  If you want to turn your machine into a distro whore, then break up the large windows partition into several smaller ext3 partitions so you can install several different versions of Linux.

Regardless, you can keep your current Ubuntu installation as is, and simply mount the new partitions and make symbolic links for various directories (if needed) otherwise simply store your media on these new partitions and my mounting them, they will become part of your Linux installation.

---

