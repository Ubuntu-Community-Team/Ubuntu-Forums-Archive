---
title: "mount: special device /dev/hdb1 does not exist"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by DarkManII on 2007-11-01
Upgraded Ubuntu to 7.10 and my HDD (fat32) doesn't mount.

All I get is this:
[COLOR="Blue"]1.mount: special device /dev/hdb1 does not exist	](*,)
2.mount: special device /dev/hdb2 does not exist	](*,)
[/COLOR]

sudo fdisk -l
> Disk /dev/hda: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce5bce5b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5005    40202631    7  HPFS/NTFS
________________________________________________
[B]Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e472e46

[COLOR="Red"]This doesn't look like a partition table
Probably you selected the wrong device.[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
[COLOR="Blue"]/dev/hdb1   ?           1        3738    30025453+   c  W95 FAT32 (LBA)[/COLOR]
[COLOR="Blue"]/dev/hdb2            3739        7476    30025485    f  W95 Ext'd (LBA)[/COLOR]
/dev/hdb5            3739        7476    30025453+   b  W95 FAT32[/B]
__________________________________________________

Disk /dev/hdd: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcc81cc81

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4795    38515806   83  Linux
/dev/hdd2            4796        5005     1686825    5  Extended
/dev/hdd5            4796        5005     1686793+  82  Linux swap / Solaris


sudo gedit /etc/fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=e1e7dbbb-c1ea-464d-98b0-d4883bb38d4b /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=6285086c-9db4-45a0-8114-e84c0214e04a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hda1 /media/c ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
[COLOR="Blue"]/dev/hdb1    /media/e vfat  iocharset=utf8,umask=000  0    0[/COLOR]
[COLOR="Blue"]/dev/hdb2 /media/f vfat user,rw,users,umask=0000 0 0[/COLOR]

darkman@darkman-desktop:/media$ ls
c  cdrom  cdrom0 [COLOR="Blue"] e  f[/COLOR]  floppy  floppy0

Any help would be greatly appreciated !!!  :)

---

### Post by DarkManII on 2007-11-01
bump!

---

