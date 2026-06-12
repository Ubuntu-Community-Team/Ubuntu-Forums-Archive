---
title: "Cannot resize NTFS partition"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by Sicilianmandolin on 2007-02-17
I cannot resize my Windows XP NTFS to make room for Ubuntu. I've CHKDSK'ed as the directions instructed to no avail and am receiving the same errors... suggestions?

-------------------------------------------------------

GParted 0.2.5

Resize /dev/sda2 from 141.71 GiB to 111.72 GiB    ( ERROR )
     	
check filesystem on /dev/sda2 for errors and (if possible) fix them    ( ERROR )
     	
ntfsresize -P -i -f -v /dev/sda2
     	
ntfsresize v1.12.1 (libntfs 8:1:0)
Using locale 'en_US.UTF-8'.
Device name : /dev/sda2
NTFS volume version: 3.1
Cluster size : 4096 bytes
Current volume size: 152157999616 bytes (152158 MB)
Current device size: 152158003200 bytes (152159 MB)
Checking filesystem consistency ...
Accounting clusters ...
Cluster accounting failed at 146839 (0x23d97): extra cluster in $Bitmap
Cluster accounting failed at 146840 (0x23d98): extra cluster in $Bitmap
Cluster accounting failed at 146841 (0x23d99): extra cluster in $Bitmap
Cluster accounting failed at 146842 (0x23d9a): extra cluster in $Bitmap
Cluster accounting failed at 146843 (0x23d9b): extra cluster in $Bitmap
Cluster accounting failed at 146960 (0x23e10): extra cluster in $Bitmap
Cluster accounting failed at 146961 (0x23e11): extra cluster in $Bitmap
Cluster accounting failed at 146962 (0x23e12): extra cluster in $Bitmap
Cluster accounting failed at 146963 (0x23e13): extra cluster in $Bitmap
Cluster accounting failed at 146964 (0x23e14): extra cluster in $Bitmap
ERROR: Filesystem check failed! Totally 24 cluster accounting mismatches.
This software has detected that your NTFS is corrupted. Please run chkdsk /f
on Windows then reboot it TWICE! Important, don't forget the /f parameter!
Afterwards you can run ntfsresize. No modification was made to NTFS.

========================================

Create Extended Partition #1 (extended, 30.00 GiB) on /dev/sda

========================================

Create Logical Partition #2 (ext3, 20.00 GiB) on /dev/sda

========================================

Create Logical Partition #3 (ext3, 8.00 GiB) on /dev/sda

========================================

Create Logical Partition #4 (linux-swap, 2.00 GiB) on /dev/sda

========================================

---

### Post by wickstopher on 2007-02-17
The graphical version of gparted included on the ubuntu edgy 6.10 liveCD worked just fine for me when resizing my xp partition to make room for ubuntu.

You could also try using the gparted liveCD.  It can be downloaded here: [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php").    I have used this to resize partitions (both shrinking and growing) very successfully.

hope this helps!

---

### Post by confused57 on 2007-02-17
The gparted live cd is very capable of resizing NTFS, probably better than the gparted version on the live cd...make sure you defrag your NTFS partition, before trying to resize(maybe even twice.

---

