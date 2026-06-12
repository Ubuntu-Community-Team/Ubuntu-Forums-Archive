---
title: "copy my dual boot disk to a disk of higher capacity?"
date: 2013-11-15
forum: Installation &amp; Upgrades
---

### Post by lithiumKid1976 on 2013-11-15
Hi

I’m looking to move my 64GB ssd disk (dual booted to win 7 and ubuntu) to a 128GB ssd disk.

I really don’t want to re-install either OS... is there a way to take an image of disk 1 and transfer it to disk 2.

also, my current linux partion has only 1.5GB of free space.. if i was to clone my original disk, how easy or feasible is it to extend the space linux disk size on the new disk?

thanks.. 

D

---

### Post by TheFu on 2013-11-15
Sure you can make it bigger. There are 50 different ways to accomplish  moving the data over. Create the new partitions of the same type and order from the old, just change the size.

To copy the data ... 
* fsarchive
* dd
* ddrescue
* gparted
* rsync
* backup and restore
* ....

---

