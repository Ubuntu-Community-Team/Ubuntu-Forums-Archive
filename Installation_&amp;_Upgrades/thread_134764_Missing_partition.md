---
title: "Missing partition"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by boss429 on 2006-02-22
I just installed Ubuntu yesterday.  I have it set up as a dual boot with Windows 2000.  My first hard drive is a 20GB FAT32 with Windows 2000 on it.  I had a second 30GB NTFS hard drive that I had used about 8 GB of.  I told Ubuntu it could use 20GB of my second hard drive.  When I boot in Windows now it says that the second hard drive isn't formated at all.  I expected it to have a 10 GB NTFS partition and then a 20 GB Linux partition (and a swap partition).  When I look at the drive in Partition Magic it says the drive is bad, which is imposible because it boots ubuntu fine.  When I run fdisk -l in ubuntu it gives me false information:
```
Disk /dev/hda: 20.0 GB, 20020396544 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2434    19551073+   c  W95 FAT32 (LBA)

Disk /dev/hdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1        2487    19976796    f  W95 Ext'd (LBA)
/dev/hdc2   *        2488        3649     9333765   83  Linux
/dev/hdc5               2        2433    19535040    7  HPFS/NTFS
/dev/hdc6            2434        2487      433723+  82  Linux swap / Solaris

```
My real FAT32 disk is hda1 not hdc1.  How can this be?  I can't seem to  figure out where my NTFS partition has gone it isn't hdc5 (or at least I can't mount it as that)
Is my NTFS partition gone?
Please help.

Thanks.

---

### Post by boss429 on 2006-02-22
I took a look at it in GParted and this is what my second hard drive looks like:
[[IMG]http://img491.imageshack.us/img491/5314/screenshot5ju.th.png[/IMG]](http://img491.imageshack.us/my.php?image=screenshot5ju.png)
I'm guessing that Unkown partition is my NTFS one, even though it seems to have the wrong file size.  Should I convert the partition to another filesystem?  Will that allow me to read it or will it erase it?

---

