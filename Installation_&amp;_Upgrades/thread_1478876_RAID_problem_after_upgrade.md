---
title: "RAID problem after upgrade"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by aadrien on 2010-05-10
Well, I have a NTFS raid1 partition from before I installed Ubuntu 9.10.
It worked well.
Yesterday came an upgrade to 10.04. Why not?
All my 500Gb of work on my raid array cannot be mounted anymore.

Here is the situation

```
dmraid -r
/dev/sdd: jmicron, "jmicron_sauvegarde", mirror, ok, 976748544 sectors, data@ 0
/dev/sdc: jmicron, "jmicron_sauvegarde", mirror, ok, 976748544 sectors, data@ 0
```
```
ls -lh /dev/mapper
total 0
crw-rw---- 1 root root  10, 59 2010-05-10 11:29 control
brw-rw---- 1 root disk 252,  0 2010-05-10 12:05 jmicron_sauvegarde
```
```
fdisk -l /dev/mapper/jmicron_sauvegarde 

Disk jmicron_sauvegarde: 500.1 GB, 500095254528 bytes
255 heads, 63 sectors/track, 60799 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk jmicron_sauvegarde doesn't contain a valid partition table
```
```
fdisk -l 

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a1b27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17495   140528556   83  Linux
/dev/sda2           17496       18241     5992245    5  Extended
/dev/sda5           17496       18241     5992213+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2cd02cd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        6374    51191122+   f  W95 Ext'd (LBA)
/dev/sdb2   *        6375       19457   105089197+   7  HPFS/NTFS
/dev/sdb5               2        6374    51191091    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```
RAID is /dev/sdc & /dev/sdd
and
```
partx -a /dev/mapper/jmicron_sauvegarde
```
does not do anything.

I have read a lot of stuff on the subject but nothing seems to work.

Any idea is welcome, I am stuck and even if I have a backup I have nowhere to restore it!

Thanks in advance

---

### Post by aadrien on 2010-05-11
OK, I got it.:(

Know I really felt why a community will never be the same as a customer support.

Depending on your question, it can happen that nobody cares. That's life.

In case some would be later interested :

I paid a data recovery service to put my stuff on a new disk they sold me.
From now on I will never use software RAID anymore but an eSata RAID device seen by my system as a black box. No driver needed, will always work.

---

