---
title: "GRUB error 15"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by ndyguy on 2006-07-22
I get this error when I boot now (using Dapper Drake Live CD).  It happened after I repartitioned half of one of my hard drives.  I have hda1 (Windows, ntfs), hda2 (Ubuntu), and hdb(Ubuntu, Swap).  I repartitioned hda2 as ext3 using gparted, and it started giving me the GRUB error 15 message after I restarted.

I found this help [http://ubuntuforums.org/showthread.php?t=43591]("http://ubuntuforums.org/showthread.php?t=43591") but it's for Hoary, and I don't want to screw things up even worse.  

"sudo fdisk -l" output:
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/hda2            5100        9729    37190475   83  Linux

Disk /dev/hdb: 8004 MB, 8004132864 bytes
255 heads, 63 sectors/track, 973 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         929     7462161   83  Linux
/dev/hdb2             930         973      353430    5  Extended
/dev/hdb5             930         973      353398+  82  Linux swap / Solaris

```

/etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 	/media/Windows	ntfs ro,dmask=0222,fmask=0333 	0 	0
/dev/hda2	/media/Storage	ext3	defaults,errors=remount-ro 0       1

```

I would appreciate any help.  Also, I'm fairly new to Linux, so small steps would help more.

---

### Post by confused57 on 2006-07-22
You could check out this link for reinstalling grub:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

or

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

You can restore the Windows mbr by booting up the Windows install CD, press "r" for recovery, then enter  *fixmbr*, which would restore the ability to boot Windows, then you could look into restoring grub to the mbr.

---

### Post by ndyguy on 2006-07-22
Thank you very much, that fixed the problem.:-D

---

