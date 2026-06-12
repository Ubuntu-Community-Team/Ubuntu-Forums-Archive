---
title: "Easy Partition Question"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by TopDawg on 2007-01-21
I have what I think is a really simple question:

When Ubuntu's partitioner asks what size to make the partition, is that your Windows partition size or your Linux partition?

PS I'm setting up a dual boot. 

Thanks ahead of time! :)

---

### Post by j19sch on 2007-01-22
It asks for the size of the partition you are creating/resizing...
If you give more details as to what you were doing, perhaps I can give a more specific answer.

---

### Post by housam on 2007-01-22
I've posted the following before and it may help you.
> I prefer to manage the partitioning manually to put every thing under control. You have to keep windows in a separate partition and create another 3 partitions for ubuntu.
Using the partitioning tool Gparted you can devide the unallocated space to the following partitions as an examples:
- 10 - 15G ext3 ( / ) for root
- 1G swap ( useless if more than 1G , you may not use it ever if you have 1G RAM or more.)
- 10-15 Gb is ext3 for /home
Remember that you can only create 4 primary partitions on your HDD. if you need more partitions you can change the 4th primary partition to be an extended one. and that one can be devided to what ever you want.
After creating the partitions you can go for the installation .  


---

