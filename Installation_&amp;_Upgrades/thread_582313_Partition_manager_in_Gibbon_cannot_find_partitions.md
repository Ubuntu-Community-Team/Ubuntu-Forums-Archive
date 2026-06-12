---
title: "Partition manager in Gibbon cannot find partitions"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by thisismike04 on 2007-10-19
My HDD currently has Vista and Feisty with GRUB running the show.  I want to clean install Gibbon without losing Vista (I messed up some things in Feisty) but the paritition manager doesn't show any partitions.  It only provides two options: Guided with the full disk or Manual, which shows sda and lets me add any partitions but does not identify the current partitions.  I really don't want to reinstall Vista because it's a pain.  

Please let me know if you have any idea what's going on.  Thank you.

---

### Post by Sokarul on 2007-10-19
This is actually a problem?  I just assumed that IDE harddrive install was different than an SATA.  I would also like to know if guided partition install while being able to adjust partition size is possible on an SATA harddrive.

---

### Post by thisismike04 on 2007-10-19
Is that the issue?  I'm on an SATA drive, but I was hoping it would work. Can anyone verify that I won't be able to reuse the same partitions on SATA, but that it would work on IDE?

Just so you know, here's my fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           14332       14593     2104483+   c  W95 FAT32 (LBA)
/dev/sda2   *           7        7957    63864832    7  HPFS/NTFS
/dev/sda3            7958       14593    53303670    f  W95 Ext'd (LBA)
/dev/sda5           14332       14593     2104483+  dd  Unknown
/dev/sda6            9233       14204    39937558+  83  Linux
/dev/sda7            7958        9232    10241374+   7  HPFS/NTFS
/dev/sda8           14205       14331     1020096   82  Linux swap / Solaris

---

