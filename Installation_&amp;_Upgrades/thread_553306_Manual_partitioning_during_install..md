---
title: "Manual partitioning during install."
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by mivo on 2007-09-17
This is a Kubuntu 7.04 problem, but I hope it is still okay to ask here (the Kubuntu forum is fairly slow).

Installing 7.04 from the Live CD with the "guided" setting works, but this only creates / and a swap partition. Once I had a running system, I put the Live CD back in and attempted to re-install with manual partitioning.

In the "Prepare Partitions" window, I deleted the existing partitions, selected the "free space" and clicked "new partition". The first partition I created was 20000 MB , ext3 and with the mount point "/" (minus the quotation marks). It was a primary partition. This worked. Next I repeated the process (same settings) different size (also ext3 and primary), picked some 227 GB (the disk is 250 GB) and typed in "/home" as the mount point. The installer tells me that I "**Can't have the end before the start**". It makes no difference whether I select the "end" radio button, or make no selection. I can add a swap partition, which will be added to the end of the list, but trying to create a partition from the "free space" in the middle and providing /home as the mount point fails.

What am I doing wrong? Is typing in / and /home for the mount points incorrect? When I look at what the installer did previously (when it created / and swap by itself), I see that the mount point for the large partition is "/media/sda1", and not "/".

The drop-down menu next to "mount point" in the partition creation dialog is empty.

Thanks for any help in advance! :)

---

### Post by mrjoeyman on 2007-09-17
I look forward to lots of answers here because I am dealing with the same types of problems installing to two different puters in different ways................

---

### Post by chameleonkid on 2007-09-17
I had the same problem. It is basically concerned with the amount your drive has and the amount it should have. I have a 250 GB drive, but its really only like 238. The installation would see this as 250 and see this extra space as a problem during manual partitioning. One of the work arounds is to boot a Gparted live cd or something similar and set up the partitions like this, because it can recognize the correct size. One you have all your partitions set up, just load the live cd and assign mount points etc and format. Hope that makes sense.

---

### Post by mivo on 2007-09-17
Thank you! That worked. :) I burnt the GParted Live CD, ran it, did the partitioning, and then changing the mount points in the Kubuntu installer was no problem. I really appreciate it!

---

