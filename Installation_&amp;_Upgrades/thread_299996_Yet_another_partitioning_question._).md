---
title: "Yet another partitioning question. :)"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by the_priest on 2006-11-15
Hi guys

I'm looking for some help on how to partition my hdd. I've done a search and read through a few posts but it's still not really solved my problem.

It's a single 80gig drive which I've split into a 40gig ntfs portion and a 40gig unpartitioned area to be used for Ubuntu.

It was lank easy to dual boot at home coz i had to drives so i just told the installer to use the second drive. But i don't have that option at work and i can't make a mistake coz i don't want to screw my windows partition.

If i use the "use largest free space" option will it install to that 40gigs I've left open or will it install to the Xgigs left on the windows partition? Also if i chose "manually edit" what should i set it just for a completely basic setup? (512mb RAM)

---

### Post by astrix on 2006-11-15
I would prefer to choose to manually edit (well I just don't remember what the other options do), just make sure the file system for the partition you want to use is set to 40gb. Make sure you have a swap partition of file system type 'swap' - size about half a gig or maybe more, you shouldn't need more than a gig. In the next screen, it should automatically set that the ext3 partition is for root (mount point '/') and the swap partition for swap - and you're set

---

### Post by the_priest on 2006-11-16
So I just need to create those 2 partitions and the installer does the rest?

---

### Post by astrix on 2006-11-16
Oh I'm sorry, I said "file system set to 40gb". I meant the 40b partition should be the ext3 file system.

Yes, provided you have a ext3 partition and a swap partition, it should automatically set the 40gb to the "/" mount point and the swap partition as well, swap. The windows partition will be set to /media/hda1 or something. You can make the mount point /media/windows if you like.

---

