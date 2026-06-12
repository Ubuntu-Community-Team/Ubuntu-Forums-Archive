---
title: "How do you dual boot XP with Ubuntu? (With Partition Magic)"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by pavel1104 on 2007-05-20
I have Partition Magic 8.0 and I have XP (Which I cannot change since I need it for school). Can someone tell me how to use PM to make a partition and install Ubuntu without messing up with XP. I am somewhat good with computers, but I have never done this before. If anyone can help, that would be great.

---

### Post by merlinus on 2007-05-20
First of all, defrag your windows partition.  Then you can use the Ubuntu live cd, which will allow you to re-size your windows partition and create others during installation.

Ubuntu will need at least partitions for / and /swap, but I advise you to create another one for /home.

You do not need PartitionMagic for this.

Good luck!

-merlin

---

### Post by pavel1104 on 2007-05-20
> **merlinus said:**
> First of all, defrag your windows partition.  Then you can use the Ubuntu live cd, which will allow you to re-size your windows partition and create others during installation.

Ubuntu will need at least partitions for / and /swap, but I advise you to create another one for /home.

You do not need PartitionMagic for this.

Good luck!

-merlin

by the Ubuntu live cd I hope you mean the iso that you download from the site right?

---

### Post by merlinus on 2007-05-20
Yes, and be sure to burn it as a disk image and not a data cd.

-merlin

---

### Post by aysiu on 2007-05-20
I've heard bad things about using Partition Magic for a Linux installation. I don't know why, but I've seen people say that multiple times on the forums.

Luckily for you, Ubuntu comes with its own partitioning software during the installation.

---

### Post by Mad_Max_1412 on 2007-05-21
Hi Everyone,

I'm in a similar situation.  Currently I've got a WinXP computer with the following setup:

Sata Drive 1:

Partition # 1: ~40GB Drive (Drive C) for WinXP and Applications
Partition # 2: Remainder (Drive D) for user files

Sata Drive 2:

Only 1 partition (Drive E), used as a backup for Drive D (see above).  That way if Sata drive 1 bites the big one, I've still got my user data.

IDE Drive 1:

Only 1 partition (Drive F) as it's only 60Gb and used to backup my laptop to.


Anyway, I used the LiveCD to boot up into Ubuntu last night and was impressed with it, although I only spent about 30 minutes in it as I had other things to do (dinner etc).  Liked how I was able to access the internet without any setup etc.

One thing that did go south was that once I re-booted and went into Windows, WinXP thought it found a new device and basically screwed up my VideoMate DVB-T300 install so it lost all the channels and wouldn't allow me to search for them.  Finally got it going after a number of re-boots.

Anyway, I'm thinking of resizing my WinXP partition which is currently drive C of about 40GB with 20GB free.  Based on the various links I gather I can use the LiveCD to resize this partion and install Ubuntu on about 10GB.  Does this 10GB include the 500Mb someone suggested for the Swap?

My big question is with the dual boot option which apparently is installed automatically as it will detect my WinXP install - will it by default automatically boot into Ubuntu or Windows if there is no user interaction (which one)?  I need it to boot automatically into Windows as my VideoMate DVB-T300 card can automatically turn on the computer, record a show and then shut the computer down.

Whilst learning Ubuntu and migrating eventually across totally, I want this functionality to remain.

If the dual boot program automatically selects Ubuntu as the default OS, how do I change it?  I have searched some forums but haven't found this specific question (unless I'm not very good at doing searches which is quite possible).

I did notice in my 30 min exploration of Ubuntu that I didn't see anything about my VideoMate DVB-T300 card, but that's a different topic so will examine that issue later.

Kind regards

Max

---

### Post by WiFi Ed on 2007-05-21
Just a couple of comments:

If you let Ubuntu resize your XP partition XP might complain the next time you boot it up. If so, follow the prompts and let XP fix itself. All should be well after that.

By default, Ubuntu will be the default booting OS, but you can edit the /boot/grub/menu.lst file to change it to XP instead. From the terminal run:  sudo gedit /boot/grub/menu.lst

Change this part:

# array will desync and will not let you boot your system.
default		0

to

# array will desync and will not let you boot your system.
default		4

save and reboot.

---

### Post by pavel1104 on 2007-05-21
I tried the Guided resize IDE1 master, partition #1 (hda1) and use freed space and got an error, so what should I do?

---

### Post by louieb on 2007-05-21
> **pavel1104 said:**
> I tried the Guided resize IDE1 master, partition #1 (hda1) and use freed space and got an error, so what should I do?
Using GParted to shrink an XP partition has been iffy for me. Done it a handful of times 4 went fine. One (well i did get in a hurry and did not defrag before i shrank it) trash XP so bad I had to reinstall. 
    If it were me. I would use PM to shrink your XP partition leaving x amount of unused space.  
Then when you install chose the manual partition option and use GParted to create your Linux partitions in the unused space. 
You need two one for swap make it around the size of your ram. The  other for / (root) just use the rest of your space. Nice and simple. 
[GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")  GParted is used by the live CD for manual partitioning.

---

### Post by stchman on 2007-05-21
> **pavel1104 said:**
> I have Partition Magic 8.0 and I have XP (Which I cannot change since I need it for school). Can someone tell me how to use PM to make a partition and install Ubuntu without messing up with XP. I am somewhat good with computers, but I have never done this before. If anyone can help, that would be great.

Partition Magic is not needed.  The LiveCD for Ubuntu contains Gnome Partition Editor.  You can simply boot the LiveCD up and then fire up gparted.  Select the disk you wish to install Ubuntu on and create some free space.  Gparted supports FAT, FAT16, FAT32, NTFS, EXT2, EXT3 file systems.  Best of all it is free.  You can create free space by selecting the partition and select resize.  Free up about 20G of hdd space for Ubuntu.  When installing Ubuntu just select Largest Continuous Free Space option.

I recommend you do a defrag and then a chkdsk /f on all XP partitions.  This will correct any errors.

That is all you need.  You will then be able to dual boot into XP/Ubuntu.

---

