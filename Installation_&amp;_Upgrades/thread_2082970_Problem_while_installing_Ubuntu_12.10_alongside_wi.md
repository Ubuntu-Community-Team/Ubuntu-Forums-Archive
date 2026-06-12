---
title: "Problem while installing Ubuntu 12.10 alongside windows 7"
date: 2012-11-11
forum: Installation &amp; Upgrades
---

### Post by ajayveee on 2012-11-11
Hi

I've tried installing Ubuntu 12.10 alongside my windows 7 unsuccessfully.  The initial challenge was that I could not create an extended partition. The disk was dynamic. I found a primary partition which I could not understand what it was(I was sure it was not the Dell Utility  partition or the system partition) . So I deleted that partition and created an extended partition and created a couple of logical partitions to install Ubuntu. After I did this, I gave the install option from Ubuntu to install it alongside Win 7. The install ran successfully but, neither Ubuntu booted successfully nor did Win 7. I tried repairing window using Win7 boot cd but it cannot repair disk errors. 
I had simple volumes created in win 7 where I had all my data, but not all of them are readable from Ubuntu live (from usb)

following is the sudo fsdisk -l command o/p

```
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f92029b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2       109135870   976771071   433817601    5  Extended
/dev/sda3           81920     4276223     2097152   42  SFS
/dev/sda4   *     4276224   109133823    52428800   42  SFS
/dev/sda5       234967040   243355647     4194304   82  Linux swap / Solaris
/dev/sda6       243357696   976771071   366706688   83  Linux
/dev/sda7       109135872   234967039    62915584   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 8100 MB, 8100249600 bytes
12 heads, 40 sectors/track, 32960 cylinders, total 15820800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        5992    15820799     7907404    7  HPFS/NTFS/exFAT

```following is the gparted partition table [IMG]https://lh3.googleusercontent.com/-S6ZAz9RpG7k/UJ9WQ4N9p_I/AAAAAAAAC9U/96B_G6pdGAc/s777/Screenshot+from+2012-11-11+07%3A28%3A37.png[/IMG]


Will I be able to recover my data? I've tried ntfs-3g options but hasnt proved to be a success. I've been able to copy some of the data in the windows volume that I want to recover, but some of the folders give an input/output error. Please help.

---

