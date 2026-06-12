---
title: "trying to recover lost partition on dual boot 12.04-Windows 2000"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by tenti on 2013-10-14
I had installed ubuntu 12.04 on a previously existing Windows 2000 partition. Used it for a long time without any problems, then I had the bad idea of defragmenting in W2000 and now the boot does not show Ubuntu anymore.
This is what fdisk is showing
ubuntu@ubuntu:~$ sudo fdisk -lu
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x031f031f

I tried TestDisk but to no avail. I am running out of ideas, I am only hopeful that everything is still there because in W2000 when I analyze the drive I see a big system files area which is about the size of the lost partition but I have run out of ideas on how to try to recover it. 
Thanks for your help.

---

### Post by mastablasta on 2013-10-14
you ran defragment on ubuntu part of the disk?

it doesn't seem like partition remains. i never did this in linux, but in windows there is a tool to repair partitions called partition doctor (not free). it could be that only partition table got damaged.

---

