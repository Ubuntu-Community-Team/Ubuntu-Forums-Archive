---
title: "Ubuntu 10.10 installation effect partitions and does not boot."
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by AndreLeComte on 2010-10-30
A fresh installation of Ubuntu 10.10 resulted in the following hard disk partitions and a system that will not boot:

> Disk /dev/sda: 12188 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
llseek: Invalid argument

sfdisk: seek error on /dev/sda - cannot seek to 387715582
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1   *     1  95609  95609   97903616    7  HPFS/NTFS
/dev/sda2     189314+ 191221-  1908-   1953089    5  Extended
/dev/sda3     95610  189314- 93705-  95953120   83  Linux
/dev/sda4         0      -      0          0    0  Empty

Disk /dev/sdb: 12188 cylinders, 255 heads, 63 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /dev/sdb: unrecognized partition table type
No partitions found

Is it possible to recover Windows Vista (an NTFS containing many important documents) which is supposed to be remaining on one of the hard disks?

---

### Post by AndreLeComte on 2010-12-16
I downloaded Active@ Boot Disk from [www.ntfs.com](www.ntfs.com) and I can see that my files still exist. I will try install an operating system on the empty drive and recover the files manually.

---

