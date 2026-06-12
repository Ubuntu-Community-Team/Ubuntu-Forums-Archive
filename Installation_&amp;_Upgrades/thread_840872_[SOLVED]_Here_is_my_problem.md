---
title: "[SOLVED] Here is my problem"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by McTek on 2008-06-25
When I did a fresh install of 8.04 the icons for my other partitions did not appear. I made a post about 2 wks ago under general help asking if anyone knew how to get the icons back on the Desktop at boot up. I had one response but I was unable to make that work. There have been no responses since. Does this mean there in no fix under 8.04? I upgraded an install of 7.10 and the icons remained on the Desktop. Should I repost the problem to a different area? My thinking is that the post is so buried that no one sees it any more. What is the proper method of bringing it back to the attention of others? 
[http://ubuntuforums.org/showthread.php?p=5215847#post5215847](http://ubuntuforums.org/showthread.php?p=5215847#post5215847)

---

### Post by cdtech on 2008-06-25
Post your "sudo fdisk -l" and can you post your "/etc/fstab" as well?

After you modify your fstab, issue the command mount -a and you should have your icons on the desktop, if your fstab file is setup correctly.

---

### Post by McTek on 2008-06-25
> **cdtech said:**
> Post your "sudo fdisk -l" and can you post your "/etc/fstab" as well?

After you modify your fstab, issue the command mount -a and you should have your icons on the desktop, if your fstab file is setup correctly.

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12d412d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1497    12024621    7  HPFS/NTFS
/dev/sda2            9105        9729     5020312+  49  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sda3            1498        6161    37463580    5  Extended
/dev/sda4            6162        6392     1855507+  da  Non-FS data
/dev/sda5            2751        4140    11165175    b  W95 FAT32
/dev/sda6            4141        5969    14691411   83  Linux
/dev/sda7            5970        6161     1542208+  82  Linux swap / Solaris
/dev/sda8            1498        2749    10056627   83  Linux


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=060a619a-40c5-4be9-af87-86ac9848e6f0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda7
UUID=70683d94-88b3-458b-980f-e022facf4c43 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by cdtech on 2008-06-25
You just need to create directories within your /mnt directory to mount each partition.

Add each partition to your fstab file:
```
########## home partition sda6 - 40G
UUID=aed3efe3-53d1-4b88-9c36-c87678436f45 /mnt/sda6           ext3    defaults        0       2

########## windows vista sdb1 - 150G
UUID=1D8FD5F25AC0301F /mnt/sdb1     ntfs    defaults,umask=007,gid=46 0       1
```

This is just an example, but use your partitions. To find the block id use:
blkid on a command line. After you add all the partitions to your fstab file and have the directories setup just do mount -a to mount all the partitions to their respective directories.

Hope this helps.....

---

