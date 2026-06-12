---
title: "Many installation sizes in Ubuntu!?!"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by nisargshah on 2010-06-17
Hi, I have a PC with 80GB hard drive with 4 partitions. I want to run Ubuntu within Windows (XP) with free space of 9GB but it gives me an option of installing in 4 different sizes (3GB,  5GB, 7GB & 8GB. What are the major differences in these four sizes of installations?

Thanks in advance!

---

### Post by tommcd on 2010-06-17
How big are these partitions?
Are they all primary partitions? Or are 1 or more logical partitions?
When you boot the Ubuntu CD, open a terminal: (applications > accessories > terminal) and post the output of:
```
sudo fdisk -l
```
This will list your partitions.
How are you choosing to partition Ubuntu?
If you choose manual partitioning, you can delete any of the 4 partition(s) that you no longer need. Then you can install Ubuntu to the newly created free space.
There is no difference in the various sizes in terms of the Ubuntu system that will be installed. The only difference is the size of the root partition.
If you just want to try out Ubuntu, then a root partition of 10GB and a swap partition of 1GB would be a good start. You could get by with 6-8GB if you can not spare that much space, and you just want to try Ubuntu.
Using 3GB is too small for Ubuntu's root partition. You will not have much space left after the install for updates and extra software. Ideally, you should have a separate /home partition for your data files (music, video, text, etc), but you could go with just a root partition (which includes /home) if you just want to try Ubuntu.
You will need to create some free space for Ubuntu. You can either resize one of the partitions depending on how big they are. Or you can delete some partitions to create free space for Ubuntu.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by leorolla on 2010-06-17
@Tommcd,
It seems he is talking about Wubi.

@nisar,
Check with the other partitions and see if some of them has more free space.
In principle 4GB is enough, but you will run out of space as soon as you start installing software etc.

---

