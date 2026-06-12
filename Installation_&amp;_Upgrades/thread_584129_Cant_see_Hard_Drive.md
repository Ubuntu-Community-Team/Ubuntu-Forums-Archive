---
title: "Cant see Hard Drive"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by dontgetshocked on 2007-10-20
hard drive does not show up.I had to re-install ubuntu and had it use the free space on the drive.Trying to get my old data off the old partition.The old partition does not show up? Here is my Fstab;

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remountro
0 1
/dev/hda6 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

Can I change or add anything here to make it work and do i have to re-boot or log off to make it work?

---

### Post by maxweld on 2007-10-20
Looks like you need to mount the old partition.

You need to know what its designation is, perhaps hda1.

Can you use the Partition Editor to see what partitions are available and see if you can identify what it was called.

Create a directory in the root directory where you can mount it.

```
sudo cd /
sudo mkdir mount
```

then mount the partition that uoi have identified

```
sudo mount -t ext3 /dev/hda1 /mount
```
assuming that it is hda1

---

### Post by dontgetshocked on 2007-10-20
Here is my fdisk info, what do I change or add? Thanks so much!

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot Start End Blocks Id System
/dev/hda1 1 4293 34483491 83 Linux
/dev/hda2 6883 7296 3325455 5 Extended
/dev/hda3 * 4294 6882 20796142+ 83 Linux
/dev/hda5 6997 7296 2409718+ 82 Linux swap / Solaris
/dev/hda6 6883 6996 915642 82 Linux swap / Solaris
Partition table entries are not in disk order
elliott@elliottlaptop:~$

---

