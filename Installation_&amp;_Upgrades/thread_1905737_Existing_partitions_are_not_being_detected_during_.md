---
title: "Existing partitions are not being detected during installation"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by aman41907 on 2012-01-07
Hi,
    I am trying to install ubuntu 11.10 over windows 7.I have 160 GB hardisk which is divided in 4 partitions and arround 30 gb unallocated space.But when I try to install ubuntu ,My partitions are not being detected.Even gparted is not able to detect the partitions.

The output of sudo fdisk -lu is

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdd36dd36

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81915434    40957686    7  HPFS/NTFS/exFAT
/dev/sda2        81915435   312560639   115322602+   f  W95 Ext'd (LBA)
/dev/sda3       163830933   245746304    40957686    7  HPFS/NTFS/exFAT
/dev/sda5        81915498   103410404    10747453+   7  HPFS/NTFS/exFAT
/dev/sda6       103410468   163830869    30210201    b  W95 FAT32

Disk /dev/sdb: 4012 MB, 4012900352 bytes
120 heads, 55 sectors/track, 1187 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     7837695     3918832    b  W95 FAT32

Disk /dev/mapper/live-rw: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders, total 8388608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O si GiBe (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/live-rw doesn't contain a valid partition table

Disk /dev/mapper/live-osimg-min: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders, total 8388608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/live-osimg-min doesn't contain a valid partition table

when i run gparted I get following information

file system : unallocated

Size: 149.05 Gib


Any help is appreciated

---

### Post by oldfred on 2012-01-07
It looks like your sda3 a primary, is inside the extended partition which is not possible. Only logical partitions can be inside the extended.

You may be able to change it to a logical.

Back up partition table first with this and save this file to another device:
sudo sfdisk -d /dev/sda > parts.txt

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

