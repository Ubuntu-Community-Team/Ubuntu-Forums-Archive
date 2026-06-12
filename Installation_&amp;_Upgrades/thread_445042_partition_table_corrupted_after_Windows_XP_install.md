---
title: "partition table corrupted after Windows XP installation"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by Hauke on 2007-05-15
After trying to install Windows XP, but aborting it the MBR was overwritten but I have resolved the problem. No the partition table is corrupted and gparted doesn't work. 

But booting the hard disk and running the Ubuntu on it is working as always and before trying to install Windows XP gparted and qtparted were working very well. 

QTparted (version from Ubuntu feisty) returns me "Critical error during ped_disk_new" and doesn't show any partition information for my first hard disk only for the second one.
And it outputs the following error:
> Error: Partitionen dürfen sich nicht überschneiden.
Ein Bug in GNU parted wurde entdeckt. Für mehr Informationen besuchen Sie bitte die Internetseite [http://www.gnu.org/software/parted/parted.html](http://www.gnu.org/software/parted/parted.html) und erhalten Sie weitere Informationen was für das Melden von Fehlern hilfreich ist. Bitte senden Sie einen Bugreport an [email]bug-parted@gnu.org[/email] unter Angabe der Version (1.7.1) und der folgenden Meldung:  Assertion (disk != NULL) at ../../libparted/disk.c:1319 in function ped_disk_next_partition() failed.

Gparted (version from Ubuntu feisty) shows me no error message, but an empty hard disk same as the version on the GParted live CD, on the second hard disk all partitions are displayed.

When writing the partition data to the disk cfdisk outputs the following message: " Wrote partition table, but re-read table failed.  Reboot to update table." But it shows the partition table.

> hauke@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   83  Linux
/dev/sda2              14       60801   488279610    f  W95 Ext'd (LBA)
/dev/sda3            9185       15410    50010313+  83  Linux
/dev/sda5              14         268     2048224+  82  Linux swap / Solaris
/dev/sda6           15411       37082   174080308+  83  Linux
/dev/sda7           37083       60801   190522836   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        5103       32130   83  Linux
/dev/sdb3            5104        5294     1534207+  82  Linux swap / Solaris
/dev/sdb4            5295       30401   201671977+   f  W95 Ext'd (LBA)
/dev/sdb5            5295        9118    30716248+   7  HPFS/NTFS
/dev/sdb6           26967       27851     7108731   83  Linux
/dev/sdb7           30129       30401     2192841   83  Linux
/dev/sdb8            9119       18042    71681998+   7  HPFS/NTFS
/dev/sdb9           18043       26966    71681998+   7  HPFS/NTFS
/dev/sdb10          27852       30128    18289971    7  HPFS/NTFS

Partition table entries are not in disk order

> hauke@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

---

