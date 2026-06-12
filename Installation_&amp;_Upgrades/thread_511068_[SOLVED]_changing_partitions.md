---
title: "[SOLVED] changing partitions"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by srcmnk on 2007-07-27
Hi, I've a dual boot with XP and Ubuntu 7.04 in two separate partitions, plus a shared NTFS for media files and the SWAP, now I'd like to try other distros without having to renounce to the two mentioned above, so I'm thinking to create a new partition to work with.
Here is the output of fdisk:

```
srcmnk@casa-machine:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1402    11261533+   7  HPFS/NTFS
/dev/hda2           19675       19929     2048287+   5  Extended
/dev/hda3           18400       19674    10241437+  83  Linux
/dev/hda4            1403       18399   136528402+   7  HPFS/NTFS
/dev/hda5           19675       19929     2048256   82  Linux swap / Solaris

Partition table entries are not in disk order
srcmnk@casa-machine:~$ 
```

now how am I supposed to do it?
Since I already have three primary partition and a logical one I can only create more logical in the already existing extended, right? But the extended partition is the last of the disk and I can only add space at the end of a partition, right again?
Is it possible to shrink hda4 (the big NTFS for sharing files), then move the hda3 with ubuntu next to it and merge all the space to the right in a extended partition i can then divide as I like?
Is Gparted live-CD a good tool to do the job?

I bit confusing, but I hope you get the point, thanks

---

### Post by srcmnk on 2007-07-27
OK, I was curious and couldn't wait...
It worked: I resized the NTFS partition then copy the ubuntu one next to it to leave free space to its right and use it to enlarge the extended partition. :)

---

