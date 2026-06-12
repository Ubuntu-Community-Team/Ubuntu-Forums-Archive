---
title: "Installer does not detect partitions"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by SourceV on 2006-09-06
I have tried to install Ubuntu today, but when I get to the partitioning stage Ubuntu does not detect existing partitions on HDB, which means I cannot select the appropriate partition on which I wish to install Ubuntu.

Your assistance will be much appreciated.

---

### Post by taurus on 2006-09-06
Do you have an IDE, SATA, or RAID?  Is it one harddrive and do you have anything on it like Window XP?  Have you partitioned your harddrive first?  You need to provide a little more info about your harddrive and your machine before anybody can figure out what's wrong with it.  As of right now, nobody knows what you are talking about!!!

---

### Post by SourceV on 2006-09-06
I have two physical hard drives
1.HDA with 10GB which I have on it Windows 2000 installed
2.HDB with 40GB with several partitions 2 of them are Windows 2000 partitions and 5 with another Linux distribution (Mandriva) installed, including /boot, /swap, /root and two others.

I am trying to install Ubuntu on one of the Linux partition, specifically on HDB 6.

When I try to manually choose the partition all I see is HDB without any details about the partitions. So it seems to me that Ubuntu does not detect these partitions. I had some experience with other Linux distributions and they always detect the partitions.


Please let me know if you need further information.

---

### Post by taurus on 2006-09-06
1.  Did you use the desktop CD (LiveCD) to install Ubuntu?

2.  Did you pick the manual partitioning your harddrive?

---

### Post by SourceV on 2006-09-06
Please see hereunder

> **taurus said:**
> 1.  Did you use the desktop CD (LiveCD) to install Ubuntu?


2.  Did you pick the manual partitioning your harddrive?

yes and yes

---

### Post by taurus on 2006-09-06
Maybe you want to use the alternate CD (same place that you downloaded the desktop CD) to install Dapper because it gives you more control of your harddrive when you get to the partition part.

---

### Post by SourceV on 2006-09-08
> **taurus said:**
> Maybe you want to use the alternate CD (same place that you downloaded the desktop CD) to install Dapper because it gives you more control of your harddrive when you get to the partition part.

Thank you for the advice, but the same problem reoccurs in the text installation mode. It just wouldn't recognize any partition on the second drive.

Any other suggestions?

---

### Post by shinsplints on 2006-09-08
I'm having the same problem.  I have the following partitions: 2 ntfs (one is for windows the other for data), 1 linux, 1 linux swap.  When I try to partition (both on liveCD and on alternate 6.06.1) It lists only the entire drive, not any of the partitions.  If I fdisk /dev/hda it shows all of my partitions.  I wouldn't mind just doing the partitioning myself in fdisk and manually setting the install point, but I can't figure out how to do that.

The hard drive is SATA, The Board is a  ASUS P5LD2 Deluxe Socket T:
North Bridge Intel 945P and South Bridge Intel ICH7R.  Any idea if there is an incompatibility with the SATA controller or such that would cause this problem?  I'd like to try edgy, but edgy knot 2 doesn't give me any video when I boot liveCD and I haven't had time recently to figure it out.

The question I'd most like answered is: is there a way to manually set the install point given that I can already partition my drive properly using fdisk? (sorry if this question hijacks the thread, but if I could it would be a fairly easy work-around).

Thank You

---

### Post by SourceV on 2006-09-08
You are not hijacking anything, apparently this version has a problem in recognizing partitions (it detects the only partition I have on my first HD).

I don't even need to make a new partition, I have it ready. I just wanted to check this distribution, as I have heard good things about it.
(I currently use Mandriva Linux which works great on my machine).


I hope somebody who knows what to do will come around before I give up on Ubuntu.

---

### Post by ariel on 2006-09-15
I'm having exactly the same problem.

I have a Dell Latitude D620 laptop, It has a single SATA disk, with existing NTFS and FAT32 partitions and lots of free space. 

When I boot with Dapper 6.06.1 Live DVD and launch the graphical installer, the disk is detected but not any of my existing partitions. The installer shows an empty, non partioned, totally unallocated disk.

Curiously, if I launch Nautilius via Places > Computer, my NTFS and FAT32 volume labels are shown!!

I tried launching the installer in text mode: exactly the same problem. I am disappointed with this, I didn't expect to run into this issue.

Any suggestion, anyone?

---

### Post by DeviouSimon on 2006-09-15
I too, am having a similar problem. This is my third install from the Ubuntu CD in the past week (still learnig). My first and second installs recognized the partitions on my hard drive but the third installation did not. I have one 160G hard drive. 30G for WinXP and the rest for Ubuntu.

---

### Post by DeviouSimon on 2006-09-15
I used the desktop cd with the manual partitioning btw. Same way as the last two times. This is very discouraging, I have up to this point had no problems with ubuntu. Sorry to double post.

---

### Post by ariel on 2006-09-16
Just to report that I tried Edgy Knot 2, booted reasonably well in my Latitude D620, but the graphical installer & the text mode installer failed to detect any of the existing partitions in the SATA drive.

I opened a bug in launchpad for this (Bug #60639)

Today I tried booting the laptop with Knoppix 5.0.1 (kernel 2.6.17); same results: Knoppix desktop shows icons for all my existing partitions; but when I try to install it to the hard disk, the partitioner (qtparted) does not detect any existing partition, and shows the disk as fully unallocated. This looks like lack of support for this type of disk at the kernel level. :(

---

### Post by ariel on 2006-09-20
Any ideas, anyone ?? I can't install ubuntu in this machine until I get the installer & grub to recognize the exisiting partitions... :(

  ](*,)

---

### Post by Malevolution on 2007-02-02
I'm seeing exactly the same problem with edgy eft.  I'm trying to install on an Inspiron 1501 with the stock HDD setup -- 60 gig, 5400 rpm "sata" at least as they put it.

No matter what I do, Ubuntu does not see *any* partition on it.  I have 30 gigs of it etched out for Windows XP (a dreadful necessity), and with the remaining space I've tried a couple of things to try to get ubuntu to recognize the HDD.

Sabayon sees the entire HDD just fine, including Windows' NTFS partition.  With GParted on Sabayon I've tried the following with the non-Windows 30 gig portion:

Two 15 gig partitions on reiserfs -- nothing found by ubuntu
One 15 gig partition on ext2, the remaining 15 gigs raw / unformatted -- nothing found by ubuntu

Laughably, I'm writing this to you on a livecd kubuntu boot  :/

As I'm new to linux (since a passing familiarity with freebsd some 12  years ago), I wanted to try Ubuntu because it's hailed as the best for newbies -- Sabayon, the first I've tried, is a friend's favorite that I just don't have the knowledge to play with now.  It sees the partitions, though  :/

---

### Post by Sebs0r on 2007-02-05
You guys read the post about the irqpoll? im not sure if this issue relates to you, but i couldnt get ubuntu to recognise the harddrive on my inspiron 1501 until i added "irqpoll" to the boot command. 

Now i have Ubuntu installed, it just doesnt detect any of the other hardware (ie the device manager just lables all hardware as "unknown") so i was wondering if it is a driver issue or another command line thing.

---

### Post by Sebs0r on 2007-02-06
Just a quick update: I reinstalled Ubuntu using a different command line (pci=nomsi) and it installed brilliantly. No further issues. I'm posting from the laptop right now and its all very good.

---

### Post by krankes_hirn on 2008-01-06
Im having the same problem with ubuntu 7.10. It just does not detect the partitions and shows the entire CD as unallocated, though nautilus seems to detect those partitions. Has anyone come up with any solution yet_

---

