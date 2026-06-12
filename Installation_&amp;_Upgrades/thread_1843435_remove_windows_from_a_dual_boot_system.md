---
title: "remove windows from a dual boot system"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by Zipdaman12 on 2011-09-13
I know this is a famous question, but I am a bit confused still.

I have installed Ubuntu as a replacement for windows, but installed it as a dual boot (from the ubuntu installer) in case I needed anything from Windows, or couldn't figure out how to get everything working in Ubuntu.
Good news is I have figured it all out and don't need Windows any more.  I would like to remove windows, but I am having problems.

From within gparted, I have 2 NTFS partitions, sda1 and sda2
sda1 is listed as a boot partition and labeled as system reserved
sda2 is unlabeled and not a boot partition.

This is my fdisk info:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00090a0b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       24322   195256320    7  HPFS/NTFS


any and all help is always appreciated.

zip

---

### Post by MG&amp;TL on 2011-09-13
Backup files, reinstall, is the easy way. Less easy way is to boot from a partitioning tool (gparted live cd?) of some sort and use that.

---

### Post by mörgæs on 2011-09-13
Using Gparted is by far the easy way. Please post a screen shot of the partitions as seen through Gparted.

---

### Post by YesWeCan on 2011-09-13
What problems are you having? The fdisk output only shows 2 NTFS partitions and no linux partitions. Are you using Wubi?

---

### Post by Blasphemist on 2011-09-13
If you could download and run this script I think we could be more sure of our recommendations. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please post the results within code tags to make it more readable. This will tell us the detail of your partitioning and configuration for boot now.

---

