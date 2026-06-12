---
title: "Ubuntu partitioner error."
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by shoopdawoop on 2007-04-29
I'm trying to dual boot with Ubuntu 7.4 but when I try to use the manual option it gives me an error that it can't make changes to the storage device or something close to that. I have 121/250 GB left and I change it to 35 gigs and it gives me the error while its resizing the partition.

---

### Post by floke on 2007-04-29
What are you dual booting with? And how big is the partition you want to shrink? Basically, I'm thinking that if its XP and its currently large then the problem could be the pagefile. You should run a full defrag before resizing anyway. Are there any immovable files on the right of the defrag GUI? If so, then that could be it (they are the page file and the hibernate space). You could try disabling them and then resizing the partition.

Worked for me.

---

### Post by shoopdawoop on 2007-04-29
I'm dual booting with XP SP2 and the partition is 129 gigs, I'm guessing that is the problem. And my pagefile according to dxdiag is 489mb/3448.
And I've never use disc defragmenter before, what does it do? Delete unused files?

---

### Post by shoopdawoop on 2007-04-29
I made a new partition, but when I click forward it says no root file system is defined.

---

### Post by floke on 2007-04-29
You have to select the partition (left click on it). Then right click and set it as 'root' (ie select '/' from the dropdown menu). This really should be explained better. But its not. So there you go.

Hope this helps.

* EDIT * A defrag will defragment your hard drive files, so that they are not all scattered over the disk. You don't need to do this in Linux because its great.

---

