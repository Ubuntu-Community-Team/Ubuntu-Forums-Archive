---
title: "Unable to resolve UUID:new scenario"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by napster86 on 2008-09-29
**During booting a error occurs and a log is created in /var/log/fsck/chkfs**

```
Log of fsck -C -R -A -a 
Mon Sep 29 15:21:37 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=82d9776a-643b-4247-b492-359a4498c533'

fsck died with exit status 8

Mon Sep 29 15:21:38 2008
```
----------------

**This is the output of sudo fdisk -l**

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x46544653

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4183    33599916    7  HPFS/NTFS
/dev/sda2            4184       30401   210596085    f  W95 Ext'd (LBA)
/dev/sda5            4184        6794    20972826   83  Linux
/dev/sda6            6795       12016    41945683+   7  HPFS/NTFS
/dev/sda7           12017       17238    41945683+   7  HPFS/NTFS
/dev/sda8           17239       23765    52428096    7  HPFS/NTFS
/dev/sda9           23766       30339    52805623+  83  Linux
/dev/sda10          30340       30401      497983+  82  Linux swap / Solaris

Disk /dev/sde: 249 MB, 249823232 bytes
16 heads, 32 sectors/track, 953 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1         952      243630+   b  W95 FAT32
```

**My /etc/fstab file contains**

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=18e003c3-0a2d-4443-a5be-2001656c7c20 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=82d9776a-643b-4247-b492-359a4498c533 /media/disk     ext3    defaults        0       2
# /dev/sda10
UUID=ac122620-618d-4886-b786-f1383b26a53c none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
*Note:The mount point is exactly the same as the name of the folder in the media drive.*

---

### Post by WWSmith36 on 2008-09-29
What does this give you

```
ls -l /dev/disk/by-uuid
```

---

### Post by Elfy on 2008-09-29
I'd expect that you've changed the uuid of a partition - have you been working won partitions at all.

Run ```
sudo blkid
``` and check that the uuid for your partitions in fstab are still correct, change fstab if necessary ```
sudo nano -B /etc/fstab
```

---

### Post by napster86 on 2008-09-29
Im running outta time here..ill reply once my moro midterm paper is over.....


will reply asap..i really need your help...

keep track of this thread..guys

---

