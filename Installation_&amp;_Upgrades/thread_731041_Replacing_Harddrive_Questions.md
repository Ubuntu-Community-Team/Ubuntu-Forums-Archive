---
title: "Replacing Harddrive Questions"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by Wehrmacht on 2008-03-21
I have just purchased a 250 gb SATA seagate drive, my old 60 GB IDE drive will be removed, as there's no point in keeping two drives in this one box.

My question is - is there a way to copy my settings from my gutsy install over to the new SATA drive?  I believe I formatted the old IDE current drive with one partition, and no /home partition.

Summary:  I'd like to use my same settings from gutsy on my new harddrive, then remove the old 60 gb IDE drive entirely....


Also any suggestions on partitioning the new SATA 250 gb drive would be great...
              My system is as follows:  amd 64 3000+ cpu (outdated I know)  2 GB ram, 264 mb cheapo vid card on a Soltek mobo.

It's going to be strictly a Linux machine for a while... but potentially down the road I may want to run windows on it for games, when some good ones come out in a year or so.

Thanks again guys,

Chris

---

### Post by confused57 on 2008-03-21
This should give you some ideas for backing up & restoring:
[http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan](http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan)

As far as partitioning, you might consider:
Partition#1  =  15 Gb root, primary partition
Partition#2  =  50 Gb /home, primary partition
Partition#3 = approx. 175 Gb data partition, ext3, logical partition
Partition#4 = no more than 1 Gb for swap, logical partition

I would place partitions #3 & #4 at the very end of the hard drive...You can vary the size of partition #2 & #3, depending on how much you want to resize #2 to free up space for Windows...Windows needs to be installed on a primary partition.  I'm not so much suggesting you partition this way, but just giving you an idea of what may work...someone else may have a better recommendation.

---

### Post by Wehrmacht on 2008-03-21
thanks a lot for the recommendations,.. I'll get on with the reading!

---

### Post by Wehrmacht on 2008-03-22
Morning Bump before work!  

Anyone else have any suggestions/pointers for me before I take the plunge tonight?

-C

---

