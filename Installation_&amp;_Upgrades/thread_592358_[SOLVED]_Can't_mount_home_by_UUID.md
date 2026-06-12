---
title: "[SOLVED] Can't mount /home by UUID"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by ag65151 on 2007-10-26
First some info:

My fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=22cd74be-f962-46a8-91a2-db457e956e40 /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
# /dev/hda1
UUID=8616c7f3-81c0-4cbc-9ed4-4db38e189104 /media/hda1     ext3    defaults        0       2
# /dev/hda3
UUID=0f3c0398-f620-4b8e-b570-4283783a973b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

fdisk -l
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00071057

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      104391   83  Linux
/dev/hda2              14        1309    10410120   83  Linux
/dev/hda3            9208        9729     4192965   82  Linux swap / Solaris
/dev/hda4            1310        9207    63440685   83  Linux

Partition table entries are not in disk order

```

My gnome trash can doesn't "see" my /home directory. It never shows trash even when I have things in my ~/.Trash 

After reading around, I saw that it might be related to mounting by /dev instead of by UUID. So, I found the UUID of the drive and put it in fstab instead of /dev/hda4, but it couldn't mount /dev/hda4 on /home. So I changed fstab back to /dev/hda4 and it mounted fine. I am a little confused.

---

### Post by Cryptog on 2007-10-26
Try booting off of the live (install) CD and open up a terminal. Do a ls -l /dev/disk/by-uuid and see if the code matches the one in your fstab for your home directory. You may be able to do this on your current system too without using the live cd.

---

### Post by ag65151 on 2007-10-26
I was able to run the ls -l /dev/disk/by-uuid in both "regular" mode and from the LiveCD. The outputs are identical. It doesn't recognize /dev/hda4 having a UUID:

```
 ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-10-26 11:10 0f3c0398-f620-4b8e-b570-4283783a973b -> ../../hda3
lrwxrwxrwx 1 root root 10 2007-10-26 11:10 22cd74be-f962-46a8-91a2-db457e956e40 -> ../../hda2
lrwxrwxrwx 1 root root 10 2007-10-26 11:10 8616c7f3-81c0-4cbc-9ed4-4db38e189104 -> ../../hda1

```

But when I enter sudo tune2fs -l /dev/hda4 
```
tune2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   <none>
Last mounted on:          <not available>
**Filesystem UUID:          204005e9-0e83-46cf-8d0a-95f3b4f14ced**
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal filetype needs_recovery sparse_super
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              7898880
Block count:              15859712
Reserved block count:     634388
Free blocks:              11945307
Free inodes:              7859915
First block:              0
Block size:               4096
Fragment size:            4096
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16320
Inode blocks per group:   510
Last mount time:          Fri Oct 26 11:10:54 2007
Last write time:          Fri Oct 26 11:10:54 2007
Mount count:              12
Maximum mount count:      30
Last checked:             Wed Oct 24 21:31:07 2007
Check interval:           0 (<none>)
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Journal backup:           inode blocks

```
It shows a UUID. When I use this UUID in fstab, it will not mount to /home and I get all kinds of errors.

Any suggestions?

---

### Post by ag65151 on 2007-11-06
Somehow, the volume got flagged as being a LVDS volume. So, I created a new partition, copied the data to the new partition, and deleted the old partition. Now all of my partitions are mounted and mountable via UUID which has fixed my Gnome trash applet problem as well as given me a more robust system.

Hope this helps someone else. Bottom line, don't use LVDS it sets flags that are troublesome to the rest of the system.

---

