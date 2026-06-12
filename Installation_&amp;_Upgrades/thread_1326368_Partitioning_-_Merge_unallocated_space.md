---
title: "Partitioning - Merge unallocated space?"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by TBBucs on 2009-11-14
Right now, I have XP using half the disk (primary partition) and Ubuntu using the other half (logical partition).  I decided to shrink them both down and add a FAT32 partition for file sharing.  So loaded up GParted via the Ubuntu 9.10 Live CD.  I shrunk down the XP partition (which is all the way to the left of the disk), and deleted the Linux partition.

The problem is, now I have two chunks of unallocated space: one from when I shrunk the XP partition, and the other from when I deleted the Linux partition.  I can't seem to merge these together, as Linux's unallocated space is still in a logical partition (I guess, I don't quite understand that...it has the light blue border, which indicates logical partition), while XP's unallocated space does not.  I just want one huge chunk of unallocated space.

Any ideas how to make this happen?

Edit: here's a screenshot of what I'm talking about: [http://img196.imageshack.us/img196/6572/partitions.png](http://img196.imageshack.us/img196/6572/partitions.png)

---

### Post by darkod on 2009-11-14
Delete the logical partition too. That will combine all the free space into... free space. :)

PS. You already said you deleted your Linux partitions. You know you destroyed your Linux installation that way right?

---

### Post by TBBucs on 2009-11-14
How do I do that?  When I right click it, the only option it gives me is to create a new partition.

Yeah, the Linux install was fresh anyway, so I don't care if I get rid of it or not.  But I haven't actually made any of these changes yet, it's all just in GParted's preview.

Edit: Ah, just got it.  Turns out you have to right click in the tree, not the graphic, to get it all.

---

### Post by Romanrp on 2009-11-14
The same thing happened to me when  I did something similar.
The quickest and laziest solution would be to install an os on the whole hdd
But this means you will loose whatever you have left.
so wait a bit,if nothing else works.then you know what to do.
It all depends whether you can live without that extra space.
Don't you just hate when this happens? :)

---

### Post by darkod on 2009-11-14
Not too familiar with Gparted (assume you are using that) from the top of my head, but it must give you the option.

Yes, in the free space you will have option to create partition, but there must be option in Gparted to delete the partition as a whole (the logical one). Sorry, can't open Gparted right now, on Windows.

PS. You can not install anything on the whole hdd because as long as it has it marked as logical partition, the hdd is not "whole".

---

