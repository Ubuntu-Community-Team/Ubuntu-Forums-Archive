---
title: "Two swap partitions? :S"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by eRoot on 2006-06-04
As I was looking through my hardware settings for a bit, I found a weird problem:

```
barry@box:~$ sudo fdisk /dev/hda

The number of cylinders for this disk is set to 4998.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1530    12289693+  82  Linux swap / Solaris
/dev/hda2            1531        1611      650632+  82  Linux swap / Solaris
/dev/hda3            1612        4998    27206077+  83  Linux

Command (m for help):
```
I have two swap partitions?! ehhh...
hda1 is my root partition, hda2 is supposed to be my swap partition. 
I figure I must have made a (very stupid) mistake when I installed Dapper.

So, which one is actually acting as the swap partition?

```
barry@box:~$ swapon -s
Filename                                Type            Size    Used    Priority/dev/hda1                               partition       12289684        13868  -1
```

That is not the answer I was hoping for.

Is there any way to make hda1 use an ext3 filesystem and make hda2 the swap partition, without erasing the whole thing?

---

### Post by taurus on 2006-06-04
Yes.  All you have to do is change the ID of the partition.  After you run "sudo fdisk /dev/hda" from a terminal, change the ID for the first partition from 82 (swap) to 83 (linux filesystem) by hitting letter t.  Then pick 1, first partition and enter 83.  Save it and format it as ext3 again...  That's all you have to do.

Also make sure you edit /etc/fstab...

---

