---
title: "Install Ubuntu over an existing RADI0"
date: 2012-08-04
forum: Installation &amp; Upgrades
---

### Post by talaus on 2012-08-04
Hi All,

I have a computer with a RAID0 setup (2 HDDs), which previously had ArchLinux on it (not functional anymore) and stores important data. I want to install Ubuntu instead, and to keep my data in place. I really have no idea how to do it, and some reference/help would be great.

Partition table:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63      192779       96358+  83  Linux
/dev/sda2          192780     4192964     2000092+  fd  Linux raid autodetect
/dev/sda3         4192965  1953520064   974663550   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63      192779       96358+  83  Linux
/dev/sdb2          192780     4192964     2000092+  fd  Linux raid autodetect
/dev/sdb3         4192965  1953520064   974663550   fd  Linux raid autodetect

sdX2 was used as swap and sdX3 stores my data.

Again, any kind of help will be greatly appreciated. Thanks!

---

