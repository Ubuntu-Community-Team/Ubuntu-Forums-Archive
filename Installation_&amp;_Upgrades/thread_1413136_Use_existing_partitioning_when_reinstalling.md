---
title: "Use existing partitioning when reinstalling"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by MANielsen on 2010-02-22
[SIZE=2]I have a laptop running Ubuntu 8.04 LTS and I need to upgrade to the new Ubuntu, I order to get complete use of my hardware. [/SIZE] 
 [SIZE=2]Usually when I install a new version of Ubuntu, I have the opportunity to use my old partitioning, but now I can only use the entire disk or create a new partition table.[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]The laptop has other partitions that is a data and a Windows partition as I want to preserve.[/SIZE]
 

 [SIZE=3]
[/SIZE] 
 [SIZE=3]  How can I install the new Ubuntu on the old Ubuntu partition and preserve the data on other partitions?[/SIZE]
 

  
 *  Thanks  *
 *     Morten Nielsen*

---

### Post by zvacet on 2010-02-22
Using manual way you should be able to remove your root and on that free space install Karmic.

---

### Post by MANielsen on 2010-02-22
My current partitioning are not shown when choosing manual partitioning, as fare as I can see my only option is to make a new partition table.

---

### Post by darkod on 2010-02-22
It seems you have some issue with your hdd. Don't write a new partition table, that usually writes new blank partition table.
Your existing partitions data will be lost.

---

### Post by antigooner on 2010-02-22
Hi I'm very new to Linux. I've installed Karmic on my Eee PC1000 and all the system files along with the 'home' directory have gone on the first 8gb SSD leaving the second 32gb SSD untouched.

Is there a way to get karmic to mount and use the existing files and file structure on the 32gb SSD? ie; home/user etc? (Original file structure was from the default Xandros OS).

Any help, links or scripts really would be much appreciated.

Many thanks in advance
Mel
(linux & forum newbie)

---

### Post by darkod on 2010-02-22
> **antigooner said:**
> Hi I'm very new to Linux. I've installed Karmic on my Eee PC1000 and all the system files along with the 'home' directory have gone on the first 8gb SSD leaving the second 32gb SSD untouched.

Is there a way to get karmic to mount and use the existing files and file structure on the 32gb SSD? ie; home/user etc? (Original file structure was from the default Xandros OS).

Any help, links or scripts really would be much appreciated.

Many thanks in advance
Mel
(linux & forum newbie)

You can mount the 32GB SSD to be used but not as /home. It already have a home folder in the new install you created. If you wanted to use the existing /home you need to do it during the install.
I'm not sure you can add it later, and plus it's from different distro so there might be incompatibility.

---

### Post by antigooner on 2010-02-22
Thank you Darko for your very prompt response to my problem. I suspected this might be the case and backed up all my stuff in anticipation. My problem now is how to specify that configuration on re-installing"

Thanks again

Mel

---

### Post by darkod on 2010-02-22
> **antigooner said:**
> Thank you Darko for your very prompt response to my problem. I suspected this might be the case and backed up all my stuff in anticipation. My problem now is how to specify that configuration on re-installing"

Thanks again

Mel

In step 4 of the installer select Advanced (Manual) partitioning, that's the only way to do it.
It will show you all partitions and they will have Not Used mark. Linux always does that to avoid deleting your data by accident. It will never automatically use a partition even if it is a linux partition.
So you will need to click on each partition one by one, then the Change button at bottom. And for each partition select the corresponding options.
For /
Mount point /
Filesystem ext4
Format Yes (tick the box)

For /home
Mount point /home
Filesystem as it is on the current
Format NO NO NO (if you want to keep the data)

Do the same for swap

---

### Post by gadolinio on 2010-02-22
> **MANielsen said:**
> [SIZE=2]I have a laptop running Ubuntu 8.04 LTS and I need to upgrade to the new Ubuntu, I order to get complete use of my hardware. [/SIZE] 
 [SIZE=2]Usually when I install a new version of Ubuntu, I have the opportunity to use my old partitioning, but now I can only use the entire disk or create a new partition table.[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]The laptop has other partitions that is a data and a Windows partition as I want to preserve.[/SIZE]
 

 [SIZE=3]
[/SIZE] 
 [SIZE=3]  How can I install the new Ubuntu on the old Ubuntu partition and preserve the data on other partitions?[/SIZE]
 

  
 *  Thanks  *
 *     Morten Nielsen*

If you want to eliminate the old ubuntu installation in order to place the new one there, try using gparted from a liveCD. Turn on the pc with  livCD, choose to try ubuntu. In the live session go to system--> administration--> gparted partition editor. You'll see a bar representing your hard disk(s). Right-click the one where you have the old ubuntu and delete it. That space will become "unassigned". Then click apply changes. Close gparted, and double-click the install icon on the desktop, and tell the program to install in the unassigned space.

---

### Post by MANielsen on 2010-02-24
Hey, thank you for your answer.
But gparted just state that my hardisk is "unallocated". I belive that I need some way to restore my partition table... but how:-)

---

### Post by darkod on 2010-02-24
> **MANielsen said:**
> Hey, thank you for your answer.
But gparted just state that my hardisk is "unallocated". I belive that I need some way to restore my partition table... but how:-)

TestDisk. But I don't know how to use it. Fortunately I never needed it. :)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by MANielsen on 2010-02-27
[TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") where the solution.
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

I scanned my HDD, chose the partition I wanted and wrote it to the disk.
Here is a forum thread that guided me: [http://ubuntuforums.org/showthread.php?t=413745](http://ubuntuforums.org/showthread.php?t=413745)

---

### Post by gadolinio on 2010-02-27
Once gparted shows your partition as unallocated, can you execute the installer, and make it install ubuntu in that unallocated space? try that. When asked, select the option of manual installation and choose the unallocated space. can you?

---

### Post by MANielsen on 2010-02-28
Yes I can
and I did that

---

