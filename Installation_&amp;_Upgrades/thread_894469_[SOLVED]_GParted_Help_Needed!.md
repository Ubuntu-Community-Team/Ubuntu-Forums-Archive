---
title: "[SOLVED] GParted Help Needed!"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by jimmysheldon on 2008-08-19
Ok. Here is my situation. I have 2 hard drives in my PC, and i'd been running windows fine using both of them. I then decided to try Ubuntu, so i installed it on the smaller of the drives, and i happily ran a dual boot for a few months. But now i have decided i want to take the plunge and go 100% ubuntu. So i burnt my copy of gparted live this morning, and delete the partition on the larger of my drives, so now i just have an unalocated drive. What i'd like to know how to do is to let ubuntu use this drive. Do i need to create a new partion? if so should it be extended? i don't even know if i'm going about this the right way, as i'm quite a novice when it comes to this stuff. so any suggestions, tips and advice is welcome! thank you, jimmy

---

### Post by Sef on 2008-08-19
> So i burnt my copy of gparted live this morning, and delete the partition on the larger of my drives, so now i just have an unalocated drive. What i'd like to know how to do is to let ubuntu use this drive. Do i need to create a new partion? if so should it be extended?

It depends on what you want to do with it.  If you want to just have it as a back up hard drive, then one or maybe two partitions will be fine.  If you wanted to try out other distributions, then I would make an extended partition.

---

### Post by jimmysheldon on 2008-08-19
well for the moment i'd to just have it at extra space to use. I was thinking maybe just having all music and homework on one drive and all games on another, just to keep it more organised. but at the moment i can't use it at all.

i'm running hardy at the moment and am happy with it, so i'm not too bothered about installing other distros. also, i was thinking about setting up a virtual machine with xp on it. there's a few things i'll eventually need to use windows for that don't need much performance, so i figured that was the best way to do it.

and oh, here's my sudo fdisk -l
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89ea89ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1ccf1cc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4787    38451546   83  Linux
/dev/sdb2            4788        4998     1694857+   5  Extended
/dev/sdb5            4788        4998     1694826   82  Linux swap / Solaris

---

### Post by jimmysheldon on 2008-08-20
managed to get it sorted now, thanks.

---

