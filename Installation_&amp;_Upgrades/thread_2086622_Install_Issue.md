---
title: "Install Issue"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by ritzz24 on 2012-11-21
I am trying to dual booth ubuntu along with windows7. in the UI as per in most of the forums, i get the option to install ubuntu inside windows7 instead of installing it alongside windows7. what's the difference and will my windows data be safe if i do so ?
i even tried installing it by doing SOMETHING ELSE. but am too confused with my partitions. any suggestions are welcome :)

---

### Post by 2F4U on 2012-11-21
I only know the option of installing Ubuntu inside Windows in combination with Wubi.

[http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)

When you choose to install Ubuntu alongside Windows a seperate partition is created and Ubuntu chooses a default setup. And finally, the something else option lets you choose how to create and size the partitons.

In my opinion, the major drawback of Wubi is, that if there is a problem in Windows so that it won't start, you most likely also have the problem with Wubi, since it is installed inside Windows.

---

### Post by Mark Phelps on 2012-11-21
IF the PC came preloaded with Win7, and you want to install Ubuntu in a dual-boot setup in its own partitions, then read through the details below BEFORE you attempt the install:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

