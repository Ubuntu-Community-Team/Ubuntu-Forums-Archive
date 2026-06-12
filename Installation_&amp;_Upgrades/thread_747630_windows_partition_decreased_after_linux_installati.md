---
title: "windows partition decreased after linux installation"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by axel1238 on 2008-04-06
I just did rebooted my comp with a fresh windows xp. I partitioned my whole hard drive for it which is 120 gigs. After I finished installation of windows I installed Ubuntu 7.10 linux. I only partitioned 20 gigs for linux but then when I logged onto windows it only shows 20 of free space. where did the rest of the gigs go? O.o

---

### Post by Partyboi2 on 2008-04-06
Have you checked your partitions with gparted (System>Admin>Partition Editor) to make sure they are the correct size? for both the windows and ubuntu partitions?

---

### Post by axel1238 on 2008-04-07
i dont see "partition editor" under administration..

---

### Post by surfed on 2008-04-07
what does this tell you:

sudo fdisk -l

---

### Post by axel1238 on 2008-04-07
it shows me this when i do sudo fdisk -l

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x358a4db0

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2932    23551258+   7  HPFS/NTFS
/dev/hda2            2933       14452    92534400   83  Linux
/dev/hda3           14453       14946     3968055    5  Extended
/dev/hda5           14453       14946     3968023+  82  Linux swap / Solaris

---

### Post by surfed on 2008-04-07
ok, so you have hda1 22g windows, hda2 90g linux and hda5 almost 4g of swap? Thats no good :)
4 gigs of swap is overkill and it seems like that you resized hda1 (windows) to 22g rather then creating 20g for linux. You can install gparted (sudo apt-get install gparted) and use it to resize stuff to more desireable sizes.

---

