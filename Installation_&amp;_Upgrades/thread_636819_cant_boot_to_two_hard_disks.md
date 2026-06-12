---
title: "cant boot to two hard disks"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by liopard on 2007-12-10
i tryed to use the Mounting Windows Partitions in Ubuntu page but im gating difrant things than i see in the intraction page ... i instuld ubuntu 7.04 after i instuld i cant see any of my staf and and naw i cant boot in to any thing im a rill nub need stap be stap halp this is what i got till naw


ubuntu@ubuntu:~$ fdisk -l 
 
Disk /dev/sdb: 80.0 GB, 80026361856 bytes 
255 heads, 63 sectors/track, 9729 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x8ae434bf 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *           1        9352    75119908+  83  Linux 
 
Disk /dev/sdc: 2048 MB, 2048901120 bytes 
64 heads, 63 sectors/track, 992 cylinders 
Units = cylinders of 4032 * 512 = 2064384 bytes 
Disk identifier: 0x35133513 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1               1         992     1999749+   6  FAT16 
ubuntu@ubuntu:~$ sudo fdisk -l 
 
Disk /dev/sda: 80.0 GB, 80032038912 bytes 
255 heads, 63 sectors/track, 9730 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x42044203 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1         608     4883728+   5  Extended 
/dev/sda2             609        1824     9767520   83  Linux 

whar do i go from here

---

