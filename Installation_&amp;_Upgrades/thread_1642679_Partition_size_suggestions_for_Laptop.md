---
title: "Partition size suggestions for Laptop"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by dmp2010 on 2010-12-10
I am planning to replace my hard drive in the laptop from 250gig to 500gig. I will just keep the 250gig as a backup. I like to install dual booting with Win7 and Ubuntu. Here's my plan on partitioning. Please provide suggestions.My understanding is that you can have only 4 Primary Partitions. Further, in the Extended Partition, you can create many Logical partitions. 

1. Primary 1 - 200 gig - Win 7

2. Extended 
2A. Logical 1 ~ 122 gig  - Ubuntu
   2A1. Swap 2 Gig
   2A2. /Home 50Gig
   2A3. / 70 Gig

3. Primary 2 - 150Gig Storage NTFS

4. Primary 3 - 20 Gig - Unallocated for future expansion of other partitions.

TIA.

---

### Post by oldfred on 2010-12-10
I would make root smaller & /home or a data partition larger. I have lots of programs installed in Ubuntu and have used only 6GB. It needs a lot less than windows.:)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

---

### Post by dmp2010 on 2010-12-10
Thank you oldfred. Based on your suggestion, I would make it as shown below. The reason Windows has more space is because my Canon HF21 still doesn't work in Ubuntu and videos take up great amount of space. 

1. Primary 1 - 200 gig - Win 7

2. Extended 
2A. Logical 1 ~ 122 gig  - Ubuntu
   2A1. Swap 2 Gig (same size as my laptop RAM)
   2A2. /Home 100Gig
   2A3. / 20 Gig

3. Primary 2 - 150Gig Storage NTFS (shared between both OS)

4. Primary 3 - 20 Gig - Unallocated for future expansion of other partitions.

TIA

---

