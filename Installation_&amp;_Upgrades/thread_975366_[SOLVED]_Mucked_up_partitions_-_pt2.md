---
title: "[SOLVED] Mucked up partitions - pt2"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by NEUR0M4NCER on 2008-11-08
Hi again...

So I thought i'd sorted the issue of deletion of my XP partition [here](http://ubuntuforums.org/showthread.php?t=975273), but ran into another problem.

I found [this](http://helpforlinux.blogspot.com/2008/09/auto-mount-hard-drives-on-ubuntu.html) site that recommends pysdm. I gave it a go, and now i've got drives on my desktop that shouldn't be there.

So here's the output of sudo fdisk -l :
```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c136ec4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14946   120053713+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b08da

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        8818    70830553+  83  Linux
/dev/sdb2            8819       19457    85457767+   5  Extended
/dev/sdb5            8819       16407    60958611   83  Linux
/dev/sdb6           19019       19457     3526236   82  Linux swap / Solaris
/dev/sdb7           16408       19018    20972826   83  Linux

Partition table entries are not in disk order

```
... and here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda5
UUID=6edc1065-1c2e-449b-aa7d-f27df86e0762  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda6
UUID=96473ddb-824d-487f-b627-24953ce78a3b  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sda1                                  /storage       ext3         defaults                    0  0  
/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0  
/dev/sdb7                                  /media/sdb7    ext3         defaults                    0  0  
/dev/sdb5                                  /media/sdb5    ext3         defaults                    0  0  
/dev/sdb6                                  /media/sdb6    swap         defaults                    0  0  
```

What I want is for all of the partitions to be mounted at boot, so I can set them up as Samba shares (managed to figure that one out on my own... :D). I'd also like for them to *not* show on the desktop. I previously followed aysiu's great little tutorial [here](http://ubuntuforums.org/showpost.php?p=1007731&postcount=4), but now that pysdm has been at it, i'm not sure what's what any more... :confused:

---

### Post by NEUR0M4NCER on 2008-11-08
So I think pysdm is causing at least one of the partitions to be mounted twice (or at least it tries to). Has it changed/added the mount point in fstab?

---

### Post by NEUR0M4NCER on 2008-11-08
Solved through IRC - pysdm added an extra mount point for / (root), which was doing funny things. Basically I just commented the extra reference in fstab. I didn't catch it because the first reference is the UUID at the top of fstab.

---

