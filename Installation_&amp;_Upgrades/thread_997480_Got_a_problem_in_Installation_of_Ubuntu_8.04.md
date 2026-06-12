---
title: "Got a problem in Installation of Ubuntu 8.04"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by sundarrajan on 2008-11-29
I am already having Windows XP installed in my system where my hard disk 160GB is in filesystem  of NTFS. Now i want to install Ubuntu8.04LTS along with WindowsXP having a dual boot for size allocated to ubuntu as 50GB by freeing some space in WindowsXP. During installation i cannot able to understand where the ubuntu is going to install in the harddisk.How can i specify in the Ubuntu Installation to carry out the free space 50GB that i have been allocated....Help me to install Ubuntu8.04

---

### Post by It_Was_Luck on 2008-11-30
Sounds like your unfamiliar with partitioning.

Imagine your HDD like a big pie (silly I know but this is probably the easiest way you'll get it.) Now imagine what 5o slices of your 160 slice pie is. If you want to install Ubuntu there your going to need to partition it. Chances are your HDD currently has two primary partitions and because you're going to need to make a "/" "/home" and a swap partition you'll have to create a extended partition.

So in the Live CD you got, find the program GParted in the System -> Administration Menu. It might also be named "Partition Editor"

Once your in there, grab your Windows partition, and shrink it so that the "Free space preceding" is just about 50GB. Then, it should then say "50GB of Unallocated space" Then make one big 50GB extended partition, then inside that make your main partion with the mountpoint "/" then your home partition with the mountpoint "/home" 

(and if your as confused about home folders as I was, imagine it like this... its basically a C:/Documents and Settings folder... where all your data and settings go, so a majority of the drive should be your /home folder. But do leave some room for the OS for upgrades, etc.)

Finally, make a swap partition (the filesystem type "Linux-Swap") of about 2GB or less. Then run the installer put the correct mountpoints in and install should go smoothly.

Hope this helped.

---

### Post by sundarrajan on 2008-11-30
Thanks for u r reply i have installed successfully the Ubuntu 8.04 by the procedure u mentioned.....

Sundar rajan   :guitar::lolflag:

---

