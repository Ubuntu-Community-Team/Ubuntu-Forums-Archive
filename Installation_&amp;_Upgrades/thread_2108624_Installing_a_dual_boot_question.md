---
title: "Installing a dual boot question"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by waltd on 2013-01-25
Hi all,
    I want to install a dual boot with Windows 7 and Ubuntu.  Windows 7 is already installed.  During the dual book install, I reach a point where  I allocate partition space and there is a slider to adjust the  partition space.   There is a left side and a right side that the slider  adjusts.  But there is no indication of what each side means?  What  space is the left side and what space is the right side.   Fyi, I have a  500GB hard disk drive and I want Windows 7 to have slightly more space than Ubuntu.

---

### Post by Bucky Ball on 2013-01-25
*Thread moved to **Installation & Upgrades***

---

### Post by furything on 2013-01-25
You windows install is at the left side of the display.

You should see an indication that it holds data (a small block to represent how much space is allocated). You want to move the right slider to reduce what windows is holding onto. Say move it down to 300gb.

The remaining 200gb will be used for linux partition and a swap partition (suggest 6gb for swap).

Make sure you defragment windows before doing this. Also windows 7 allows you to change the partition size from inside the disk manager.

To access right click my computer icon and select manage. In the new window select disk management and the windows disk to resize. Right click and select shrink volume. See attached image.

If you shrink the volume in windows then you can just tell ubuntu to install to free space.

---

### Post by waltd on 2013-01-25
Thank you.

---

### Post by furything on 2013-01-25
Your welcome
Hope it goes well for you.

---

### Post by Mark Phelps on 2013-01-25
Do NOT, repeat NOT, use the slider to shrink the Win7 OS partition.  Doing so risks corrupting the NTFS partition, possibly rendering Win7 unbootable as a result.

If your PC came with Win7 preinstalled, you need to read through ALL of the following before attempting the dual boot install:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

