---
title: "reinstalled ntfs partition, now can not mount it"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2007-01-07
I reinstalled XP on a ntfs partition and now can not mount it from edgy.  I've searched and read, trying  ntfs-3g but still no luck.  For some reason my mtab file is corrupt.  Any thoughts on how to diagnose problem and mount ntfs partition?

TIA

Jim

---

### Post by taurus on 2007-01-07
What does your partition table look and your /etc/fstab?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by jamaas on 2007-01-07
Thanks, here it is!

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2550    20482843+  83  Linux
/dev/hda2   *        2551        5167    21013464+   7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/hda3            5168        6996    14691442+  83  Linux
/dev/hda4            6997        7296     2409750    5  Extended
/dev/hda5            6997        7296     2409718+  82  Linux swap / Solaris


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=07D5-061E / ext3 defaults,errors=remount-ro 0 1
# /dev/hda4 -- converted during upgrade to edgy
UUID=b709b586-124f-45dc-ac8d-55419840c0e1 /media/lin2 ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=8b9d039b-2aa4-4d5f-a3f3-3048d76c209b none swap sw 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 ro,user,noauto  0   0
# /dev/hda2 -- converted during upgrade to edgy
# edited by jam UUID=92C838E2C838C66F /media/XP ntfs nls=utf8,umask=0222 0 0
/dev/hda2   /media/XP    ntfs-3g     defaults,locale=en_US.utf8   0    0

---

