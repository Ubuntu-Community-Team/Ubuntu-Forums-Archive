---
title: "Reinstalled Feisty, cannot mount 2nd internal HD (ext3)"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by al2cane on 2007-10-12
Hi, have searched thru the forums, but haven't seen this problem listed so here goes..

I have two internal hard drives, not sata, run of the mill IDE.  Feisty installed on /dev/sda, with a small swap partition, and then all my data on /dev/sdb.  I've just reinstalled Feisty onto /dev/sda, and discovered I cannot touch /dev/sdb

GParted shows /dev/sdb as being 37.27GiB, but marks the filesystem as unknown.

When I tried  "sudo mount -t ext3 /dev/sdb1 /media/40gb", I got:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Output of sudo fdisk -l
```
Disk /dev/sda: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         978     7855753+  83  Linux
/dev/sda2             979        1027      393592+   5  Extended
/dev/sda5             979        1027      393561   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux
```

I guess the question is, is all the data on the 40gb drive lost? If not, how do I get at it?

---

