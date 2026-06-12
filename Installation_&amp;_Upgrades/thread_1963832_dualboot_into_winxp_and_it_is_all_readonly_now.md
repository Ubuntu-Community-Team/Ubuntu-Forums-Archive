---
title: "dualboot into winxp and it is all readonly now"
date: 2012-04-23
forum: Installation &amp; Upgrades
---

### Post by texascfdad on 2012-04-23
i recently decided to try out ubuntu 11.10 on my compaq desktop. it has windows xp on it already and i didnt want to mess with the current set up so i used a smaller hdd to instal ubuntu on. after the install it would not boot into windows or ubuntu. the grub 2 wasnt working right. so after a couple days of messing around and reading the forums, i was able to get it all working, but destroyed my win xp recovery partition and mbr on winxp. i was able to fix that with a winxp recovery/install disk. so finally it all seems to work ok, grub2 bootloader works dual boot works fine, bothe systems come up great. im able to access my winxp files from ubuntu just fine. but when booted into windows all files are read only and there is no option to change it. i am administrator and have checked all my permissions in the security tab in safe mode. im sure it ahs something to do with linux changing permissions on it or something. but im not sure what. 
this is the result of the fdisk -l command

Disk /dev/sda: 80.1 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders, total 156368016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1a691a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    11022479     5511208+   c  W95 FAT32 (LBA)
/dev/sda2   *    11022480   156355919    72666720    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 13.6 GB, 13578485760 bytes
255 heads, 63 sectors/track, 1650 cylinders, total 26520480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004aefe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    25079807    12538880   83  Linux
/dev/sdb2        25081854    26519551      718849    5  Extended
/dev/sdb5        25081856    26519551      718848   82  Linux swap / Solaris

this is my fstab file. i added the last two entries (after backing up the original of course) as they were not in there. but all it did was auto mount them when i boot in ubuntu 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=705fd3b7-625d-43a7-9f6d-3e9704c1d4c0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cb2b02ad-b0a3-4f9c-a6dd-66a1b5900bfc none            swap    sw              0       0
#info for  5gb windows partition on /dev/sda1
/dev/sda1 /media/PRESARIO_RP auto defaults 0 0
# info for 72gb windows primary partition on /dev/sda2
/dev/sda2 /media/PRESARIO auto defaults 0 0

---

