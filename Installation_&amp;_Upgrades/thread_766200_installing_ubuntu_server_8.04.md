---
title: "installing ubuntu server 8.04"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by ssahl on 2008-04-25
I was trying to do a clean install of ubuntu server edition 8.04
I have an Asus P5E-VM DO motherboard and I'm using 4 80gb SATA hard drives setup in a raid 0 (making 2 raid drives)
the first raid drive has winXP pro on it (2 equal size partitions)
the second has one partition and the other half unallocated 
during the install it sees all 4 drives separate and doesnt see the raid 0 setup
I wanted to install to the empty space on the second raid drive
but I didnt want to lose any information/data on the first raid drive, or the partition on the second raid drive
will this version of ubuntu linux work for what I want?

---

### Post by gtdaqua on 2008-04-25
Yes it will. Install windows first and then you can install Ubuntu on any free partition or unpartitioned space. Ubuntu will automatically adjust GRUB to locate and load Windows partitions. Is available since Feisty I guess.

I have installed many times Ubuntu alongside Windows on different partitions, both physical partition and logical partitions.

At boot time, you can select which OS to load. No manual configuration is required which is very cool!

---

### Post by DukeNuke2 on 2008-04-25
linux can't see the raid devices cause it's a soft-raid. if you are not sure which drive to use, just disable the drives with winxp on them... maybe you have to pull the sata cable...

---

### Post by gtdaqua on 2008-04-25
One more thing to note is that Ubuntu will flawlessly install on any drive (logical or physical) but it has to reside on one dedicated partition. 

So you have two 160GB logical partitions. You need to create atleast 2 GB of a logical partition for Ubuntu. You can you use several tools to adjust partitions if you have already partitioned. 

Try Hiren's Boot CD - they have loads of utils to do this. They are easy too.

---

### Post by ssahl on 2008-04-25
Ok, the only problem is that it asks what drive to install on, not which partition.  I know which 2 drives are for the second raid 0 drive, but since ubuntu sees the drives seperate, will installing to a single drive mess up the raid 0?
This is assuming I pick the 'correct' drive, or should I say, the one that is associated with the empty space.

I'm not sure how it will work.  If 2 80gb drives are setup as a raid 0 and should be seen as one 160gb drive that has one 80gb partition and the rest unallocated space.  wouldnt the empty space actually be on both drives, same with the partition?

I guess I can move some data over to the first raid drive (the one with winXP already installed on it) then pick one of the drives from the second raid 0

how/where is the GRUB installed?

in other words, if I install ubuntu and all goes well and I end up with a dual boot with xp and ubuntu, what happens if I later want to remove ubuntu from my computer, or better yet, what happens if I remove the 2 drives from the second raid 0?

will winXP still boot up, or would I need to fix the MBR by running repair from the xp cd

I'm sure I can make it work, I just dont want to end up needing more then the first 2 drives on the raid 0 winXP in order to boot if I should decide to remove ubuntu or the last 2 drives on the second raid 0

does that make since?

---

