---
title: "I am trying to install ubuntu 10.4 on a pc which have already windows 7 64bit. I boot"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by osviweb on 2010-07-29
I am trying to install ubuntu 10.4 on a pc which have already windows 7 64bit. I boot from ubuntu live cd, live cd works fine but installation fails.
 Also if from Ubuntu live cd if I launch gparted it crashes. 
I guess there is some problem with the partitions. What should I do?

This pc is new and have preinstalled windows 7 64bit. It have a ntfs partition and a recovery partition.

The ubuntu I have is the one in Ubuntu homepage.

thanks

---

### Post by osviweb on 2010-07-29
I solved this by myself. It looks like the ubuntu cd was not able to view and change the Windows 7 64bit partitions.
I had to modify the partitions from a windows live cd (mini pe), set the ubuntu partitions and then install.
Gparted was not able to see or change windows7 64 bit partitions

---

### Post by efflandt on 2010-07-29
For Win7 or Vista it is recommended to use Windows own tools (in Computer Management, which you can do from a running Windows system) to shrink Windows and make room for Linux.  I did that with 64-bit Win7 and had no trouble installing 64-bit Ubuntu 10.04.

I have had no trouble shrinking WinXP ntfs partitions with gparted.  Except in that case it is recommended to temporarily disable virtual memory (similar to Linux swapfile) that might limit how far you can shrink a Windows partition, because virtual memory cannot be moved.  6 years ago I did not do that and could only shrink Windows about 24 GB on a 200 GB drive.  But more recently I disabled virtual memory and could have shrunk Windows by more than 150 GB if I wanted to.

---

### Post by osviweb on 2010-08-06
You are right. It worked using the partition tools into windows 7.

Never had this problem with xp where I could resize the partitions for Ubuntu with Gparted

---

