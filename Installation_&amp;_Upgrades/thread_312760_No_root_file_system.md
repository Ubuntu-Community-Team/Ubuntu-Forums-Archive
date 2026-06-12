---
title: "No root file system"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by bandreasen on 2006-12-04
I just purchased a copy of kubuntu 06.10 but am having installation problems.  I want to install it on a large partition of my second hard drive.  I created a partition to put it on and in the installation picked the partition management choice to make sure it got on the right partition.  However, at the step where I select the partitions I selected the swap partition and the root (/) partition but when I try to continue I get a message that says "no root file system" and the installation won't continue.  What am I doing wrong and how do I proceed?

Another general question - I read that the grub boot loader is installed at the hd0 location.  If that's the case, will I still be able to use my boot manager?

---

### Post by veli on 2006-12-04
you missed to select the root partition probably (or assigned the /root to another partition). It happened a couple of times to me when I'm not too careful. But I'm using the server install usually, no GUI, and all is done by selecting with the arrows and ENTER. Try again, and be sure to select the right partition for /root.

---

