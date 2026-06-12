---
title: "Partitioning Help"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by EricDallal on 2008-06-12
Hello,
I put up a similar post but have since run into more problems (the first two issues of concern were mentioned on a previous post, the rest is different).
I recently installed Vista as well as a bunch of applications. I did not partition the disk using the tool on the Vista boot CD because I wasn't sure how much memory I would need for Vista and all the apps. After installing most of the Vista applications, I've decided to allocate 40GB to it. I was about to install Ubuntu and run GParted, as I did with my previous computer, but then decided to look on the forums. There are four issues that concern me:

The first issue is that I have seen numerous warnings that GParted doesn't work well with Vista. I would prefer not having to reinstall everything. I have seen that it is possible to shrink the Vista partition using tools available within Vista. Unfortunately, I tried following the instructions found at: [http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista]("http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista")
but Vista wouldn't allow me to shrink the partition down enough.

The second issue is that there are already 3 partitions (C:/ drive, system volume drive, and toshiba backup drive). I didn't have this problem on my previous computer, where I simply created 4 partitions (NTFS/FAT32/ext3/linux swap).

The second issue seems to imply that I have no choice but to create an extended partition and split it into three logical partitions:
1) FAT32 shared memory partition
2) ext3 linux partition
3) linux swap partition
This leads to two other potential problems:
I read here: [http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/]("http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/")
that extended partitions should only be used for backup or storage partitions since they are not bootable. Does this mean I shouldn't install the Ubuntu operating system on the extended partition? Is there any way around this?

The last problem concerns what I read here: [http://onkarjoshi.wordpress.com/2007/04/03/partitioning-help-for-multi-booting-ubuntu-linux-and-windows-xp-safely/](http://onkarjoshi.wordpress.com/2007/04/03/partitioning-help-for-multi-booting-ubuntu-linux-and-windows-xp-safely/)
According to that article, it is a bad idea to place the FAT32, ext3, and linux swap logical partitions on the same extended partition. The article's author writes that the Windows setup crashed at the partitioning screen until he changed the extended partition to a linux extended partition. I don't see different types of extended partitions in GParted. I don't want there to be any problems with windows being able to see the FAT32 partition (I plan on allocating 120GB out of 180GB to it), or with windows crapping out on me when I try to read/write files on this partition.

Has anybody successfully placed these three logical partitions on a single extended partition (i.e., shared FAT32, ext3 with linux OS, and linux swap) on a dual boot system without any problems?

My current plan is as follows:
1) Use Gparted from Ubuntu live CD to shrink the C:/ drive down to 40GB.
2) Use GParted from Ubuntu live CD to create an extended partition on the remaining free space (with 3 partitions used I can only create one more).
3) Split the extended partition into three logical partitions (FAT32 for shared memory, ext3 for linux, and linux swap space).

Given the potential for destruction (gotta love the warning you get when you forget to put sudo before gparted), I decided it was safest to put up a post and ask for advice before proceeding.

Special thanks to anyone that reads this whole post and gives me useful advice (actually, I am thankful if anyone reads the whole post).

--
Eric

---

### Post by louieb on 2008-06-12
> Does this mean I shouldn't install the Ubuntu operating system on the extended partition? Is there any way around this?


Linux doesn't care. Primary or logical, all is good. Linux doesn't even care if the boot flag is set or not. Go ahead and create your extended partition, put Linux inside it and your good to go.

---

