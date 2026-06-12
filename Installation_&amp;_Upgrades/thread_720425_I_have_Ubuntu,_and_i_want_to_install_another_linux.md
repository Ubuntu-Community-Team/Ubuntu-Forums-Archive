---
title: "I have Ubuntu, and i want to install another linux, how can i do this?"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by emshains on 2008-03-10
I want to make new partitions on my hard disk to install other linux like Linux Mint and PClinuxOS, and then later ill maybe want to delete them. I dont know anything about partitioning, so i hope you will help me. 
 I have 160 gb sata .

P.S. Sorry for the reocuring thread, i dont have much time today.

---

### Post by confused57 on 2008-03-10
Here are some screenshots using gparted to resize partitions:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

You can use gparted with the Ubuntu live cd...System---Administration---Gnome Partition Editor.

What I've done in the past is use the gparted live cd:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

The Ubuntu live cd should work just as well as the gparted live cd...resize a partition to free up enough space(10-20 Gb?) to install another OS, you can have many logical partitions, but only 4 primary partitions on a hard drive.

Here's a guide on partitioning:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)

Booting multiple linux distros:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

Using the Ubuntu live cd to restore grub to the mbr, if you need to:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I don't have much time right now, but this should get you started.

---

### Post by emshains on 2008-03-11
When i run Gparted i cant do anything with the existing partitons, nor I can make new ones.
It Latvian, but it doesnt get rid of the fact that it wont work. This is actually got from  a normal ubuntu running, but i tried the livecd and nothing changed.

---

### Post by confused57 on 2008-03-11
> **emshains said:**
> When i run Gparted i cant do anything with the existing partitons, nor I can make new ones.
It Latvian, but it doesnt get rid of the fact that it wont work. This is actually got from  a normal ubuntu running, but i tried the livecd and nothing changed.
You can't resize a partition if it is mounted, is this screenshot taken from your installed Ubuntu, using gparted?  You "should" be able to resize the partition, using either the Ubuntu live cd or the Gparted live cd.  Are the "locks" present when you use the live cd(s)?

---

### Post by emshains on 2008-03-11
> **confused57 said:**
> You can't resize a partition if it is mounted, is this screenshot taken from your installed Ubuntu, using gparted?  You "should" be able to resize the partition, using either the Ubuntu live cd or the Gparted live cd.  Are the "locks" present when you use the live cd(s)?



Yes when i used  a liveCD it was locked too.

---

### Post by zvacet on 2008-03-11
PCLOS live Cd is good partitioning tool and you want to install PCLOS so it match your needs.Read [this](http://ubuntuforums.org/showthread.php?t=114142) but sign as root and at the end instead of** cancel** go for install.Of cource you will boot from CD and that you will set up in BIOS.

---

### Post by emshains on 2008-03-12
I will try that, but the a last question. Will all my data will be lost if i repartition a hard drive that is half full (75 free 73 used) ???

---

### Post by zvacet on 2008-03-12
No,but you have to be careful to format (make new partition) on free space.Partition tool will show you unallocated space and there you will make new partitions and do not touch part of disc which is full.

---

