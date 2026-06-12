---
title: "Wubi can't find my linux partition?"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by karasuman on 2013-06-15
I broke ubuntu trying to upgrade from 12.04 to 12.10.  I figured nothing could be worse than 12.04, but I wasn't reckoning with the upgrade failing at the very last step (restarting the computer) and reducing that partition to... I don't even know.  When I use DiskInternals linux reader, it shows the drive as simply "/" with no letter.  There's a minimal amount of folder structure, but almost no files.  When I boot into it, I think it's trying to find files but they're all gone because I didn't listen to everyone who told me never to upgrade through update center.

So, now I'm in Windows 7, trying to reinstall ubuntu on that partition.  Unfortunately, Wubi only sees the Windows partition and not the 900 GB empty partition where I want ubuntu to live.  Can anyone give me some advice?

---

### Post by cwsnyder on 2013-06-15
If you are installing to a 900 G partition, you probably need to reboot into an Ubuntu install or Live disk and install from there rather than using WUBI.  WUBI installs under Windows on the Windows partition.

---

### Post by Mark Phelps on 2013-06-15
My advice is to stay away from Wubi at this point.  Ubuntu 12.10 is the LAST version that will even support it, as it has been dropped from.  You'll be using a process that has already been abandoned.

A better approach at this point would be a true dual-boot install -- but BEFORE you do that, be sure to read through the details below:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, and you are using MBR partitioning (not GPT) that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by karasuman on 2013-06-15
Thanks very much for the advice.  I don't seem to have any spare DVDs lying around, but I can pick one up tonight and work from that.

---

