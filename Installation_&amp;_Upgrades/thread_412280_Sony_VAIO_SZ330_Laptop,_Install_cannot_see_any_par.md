---
title: "Sony VAIO SZ330 Laptop, Install cannot see any partitions"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by yalavarthy on 2007-04-17
I am trying to install Ubuntu 6.10 on Sony Viao SZ330P. It has 120G internal driver with the following partitions..

Microsoft DiskPart version 6.0.6000
Copyright (C) 1999-2007 Microsoft Corporation.
On computer: VAIO

DISKPART> select disk 0

Disk 0 is now the selected disk.

DISKPART> list partition

  Partition ###  Type              Size     Offset
  -------------  ----------------  -------  -------
  [B]Partition 0    Extended          6142 MB  8033 KB
  Partition 4    Logical           5122 MB  8064 KB  (ext3 /)
  Partition 5    Logical           1020 MB  5130 MB (Swap)
  Partition 1    Primary             25 GB  6150 MB (Windows XP)
  Partition 2    Primary             25 GB    31 GB  (Vista)
  Partition 3    Primary             56 GB    56 GB (Data)[/B]
DISKPART>

Problem is that Ubuntu disk partitioning tool see the drive but not partitions. It sees the entire drive
as unallocated space. I tried manual and automatic procedures.

Please help.

-Srinivas

---

### Post by yalavarthy on 2007-04-18
Here is what I see when I boot from CD..

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         785        4048    26218080    7  HPFS/NTFS
/dev/sda2            4049        7312    26218080    7  HPFS/NTFS
/dev/sda3            7313       14594    58492665    7  HPFS/NTFS
/dev/sda4               2         784     6289447+   5  Extended
/dev/sda5               2         654     5245191   83  Linux
/dev/sda6             655         784     1044193+  82  Linux swap / Solaris
[B]
Partition table entries are not in disk order[/B]

Disk /dev/sdb: 129 MB, 129892352 bytes
16 heads, 16 sectors/track, 991 cylinders
Units = cylinders of 256 * 512 = 131072 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         990      126703+   6  FAT16


Following screen shots explains what I have been experiencing.

Thanks for your help.

---

### Post by yalavarthy on 2007-04-20
I was able to fix this by using "sudo parted" to create a W95 LBA extended partition.
Now Ubuntu can recognize the entire partition table. Appearently it is having trouble recognizing partition created by Vista.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         785        4048    26218080    7  HPFS/NTFS
/dev/sda2            4049        7312    26218080    7  HPFS/NTFS
/dev/sda3            7313       14594    58485497    7  HPFS/NTFS
/dev/sda4               1         784     6295527    f  W95 Ext'd (LBA)


coolshoes

---

