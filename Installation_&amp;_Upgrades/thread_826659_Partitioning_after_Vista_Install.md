---
title: "Partitioning after Vista Install"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by EricDallal on 2008-06-12
Hello,
I recently installed Vista as well as a bunch of applications. I did not partition the disk using the tool on the Vista boot CD because I wasn't sure how much memory I would need for Vista and all the apps. After installing most of the Vista applications, I've decided to allocate 40GB to it. I was about to install Ubuntu and run GParted, as I did with my previous computer, but then decided to look on the forums. There are two issues that concern me:

The first issue is that I have seen numerous warnings that GParted doesn't work well with Vista. I would prefer not having to reinstall everything. I have seen that it is possible to shrink the Vista partition using tools available within Vista.

The second issue is that there are already 3 partitions (C:/ drive, volume info drive, and toshiba backup drive). I didn't have this problem on my previous computer, where I simply created 4 partitions (NTFS/FAT32/ext3/linux swap).

My current plan is as follows:
1) Use Vista's utility to shrink the space allocated to the C:/ (windows NTFS) drive.
2) Use GParted from Ubuntu live CD to create an extended partition on the remaining free space (with 3 partitions used I can only create one more).
3) Split the extended partition into three logical partitions (FAT32 for shared memory, ext3 for linux, and linux swap space).

Given the potential for destruction, I decided it was safest to put up a post and ask for advice before proceeding.

Thanks for any advice that people can give me.

---

### Post by telemarker on 2008-06-12
Hi,
I had Vista alredy installed, and wantes to install ubuntu.
I made the following:

1)With Gparted reduced the partition for vista (OS, NOT the recovery partition)
2)create an extended partition for UBUNTU, in where I put the swap and the root logical partitions. (always with Gparted)
3)Gparted automatically copied all Vista files from the newly ceated ext3 partition in the resized Vista partition (OS)

After I restarted Vista it made automatically a control that taked 15-20' and then everything worked. But make sure not to touch the Recovery partition (Toshiba Backup in your case)

---

### Post by EricDallal on 2008-06-12
Now I've got another concern. I read here [http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/]("http://vistarewired.com/2007/04/07/how-to-work-with-partitions-in-windows-vista-xp-when-disk-management-doesnt-work/")
that you can't boot off an extended partition. Does this mean the grub can't be on the extended partition or that no operating system can't be on an extended partition? Bottom line, Can I still install the linux operating system on one of the logical partitions of the extended partition?

---

