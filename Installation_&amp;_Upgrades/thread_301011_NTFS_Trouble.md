---
title: "NTFS Trouble"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by webjames on 2006-11-16
Hi, i cann't seem to mount my NTFS disks at startup. :( here is my fdisk -l:

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14762   118575733+  83  Linux
/dev/sda2           14763       14946     1477980    5  Extended
/dev/sda5           14763       14946     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      484518   244197040+   7  HPFS/NTFS


Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=8ad613fd-eabb-44c0-9b60-9fead395b882 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=085e3bc0-a01e-4030-9f6e-2d6d3c1916ac none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb1     /media/windows/driveA     ntfs-3g     defaults,locale=en_GB.utf8   0    0
/dev/sde1     /media/windows/driveB     ntfs-3g     defaults,locale=en_GB.utf8   0    0

i have set up the mount points, but the drives wont mount.

i followed this post line by line:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

still no luck :(

any ideas?

thanks, James :)

---

