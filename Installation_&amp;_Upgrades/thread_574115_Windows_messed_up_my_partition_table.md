---
title: "Windows messed up my partition table"
date: 2007-10-12
forum: Installation &amp; Upgrades
---

### Post by Ould on 2007-10-12
Hi everyone,

I decided to reintall Windows on my drive today as I recently upgraded my motherboard and my old windows install would no longer boot. Everything on the Windows side went well. I proceeded to reinstall Grub so I could get back to Linux. This is where my problems began. It seems windows reordered the partition table somehow. I.E. what was /dev/sda3 now became /dev/sda2. I can see why it did it as there was gaps in my numbering from previously deleted partitions and what not. I.E I had /dev/sda1. /dev/sda3, etc, so there was some gaps here and there. I guess windows decided to crunch everything down so they go in sequence /dev/sda1. /dev/sda2. /dev/sda3 and so on up until /dev/sda6. I have some unallocated space in there as well. This is all fine and dandy and I reconfigured Grub and fstab to mount everything properly and my linux install seems ok and all my data is in tact  but I have some other issues now it seems.

1. I cannot boot into my new windows installation. Windows is located on /dev/sda1 and is NTFS. And here is my grub entry for windows:
```
# (1) Windows
title Winblows XP
rootnoverify (hd0,0)
makeactive
chainloader +1
```
When I select this option it tries to do this but it just sits there and does nothing until I ctrl-alt-del. I don't use Windows much but installed it so I could play some of my games so I would like it to work.

2.  My partition table seems to be corrupt or gone. When I fire up gparted it shows the whole drive as "unallocated space". This doesn't seem good. :-( It was working fine right before my windows install as I checked gparted to figure out what partitions were where so I could restore grub. I even tried parted and it won't show me much. When I issue it a "print" command it returns the following:

```
Error: Can't have overlapping partitions.
```
And finally when I issue an fdisk -l I get the following:

```
omitting empty partition (5)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a80f0b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20481851    7  HPFS/NTFS
/dev/sda2            2551        2562       96390   83  Linux
/dev/sda3            2563       38913   291989407+   f  W95 Ext'd (LBA)
/dev/sda4            7905       38913   249079761   83  Linux
/dev/sda5            3200        5112    15366141   83  Linux
/dev/sda6            7663        7904     1943833+  82  Linux swap / Solaris
```
I don't see anything overlapping but I do notice the partitions are out of order. /dev/sda4 should be at the bottom but not sure if that matters or not.

I am thinking more than likely issue 1 and 2 are related but I am not sure. Any help would be greatly appreciated. I guess worst case scenario I could back up my complete drive and then redo the partitions from scratch and then copy everything back over but that seems like a lot of work and I am hoping for a simpler solution.

Kevin

---

