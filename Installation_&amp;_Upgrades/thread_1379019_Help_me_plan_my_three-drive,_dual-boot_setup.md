---
title: "Help me plan my three-drive, dual-boot setup"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by underquark on 2010-01-12
I have read many threads on setting up different partitions etc. but would appreciate any advice for my particular setup.

I currently have two 1Tb hard drives set up as follows:

Drive 1:
Windows XP in about 300Gb partition - NTFS
ubuntu 9.04 64-bit in 600+Gb partition - ext3
10 Gb swap partition (I dream of getting hibernate to work one day)

Drive2:
1Tb NTFS containing data only (pictures, videos, music)

I have just ordered a 1.5Tb drive to add to my system.

I do normal office-type tasks, rip DVDs (all backups of discs I own and which I periodically transfer to a media player), store home movies and convert and store recordings from digital TV etc.

For the moment I wish to continue using 9.04 but I want to upgrade to Lucid when it comes out.  I use VirtualBox to run some proprietary Windows software but want to keep the dual-boot to XP option as there are still a few occasions when I need it.

So, if you had this setup, what would you do and why?  Once it's stable I won't be changing anything until the next major ubuntu upgrade.

---

### Post by fancypiper on 2010-01-12
I have a desktop rather than a laptop

I think you are wasting space with a 10 Gb swap partition. I have 2 GB swap and usually it uses about 65 MB of it.

For my Linux installations I usually recommend:
/ - from 5 to 25 GB depending on the software installed and if you keep the downloaded .deb files or not.  You have plenty of room, so I would go with 25 GB if I had your hardware.

I back up the /etc and /boot directories before major changes as well.
Swap - 2 gb to be safe (I have 2 GB ram)
/home - I would use the new drive for /home
Any extra space you have left over, I would make /pub, /storage or some such.

If you have a separate /home partition, re-installation or distro hopping is easy and you won't lose the data on /home, /pub, or any separate partition if you choose to **not** format during installation.

---

### Post by tommcd on 2010-01-12
> **underquark said:**
> 
I currently have two 1Tb hard drives set up as follows:

Drive 1:
Windows XP in about 300Gb partition - NTFS
ubuntu 9.04 64-bit in 600+Gb partition - ext3
10 Gb swap partition (I dream of getting hibernate to work one day)
You should create a separate /home partition for Ubuntu. This will keep your data separate from the root partition and make reinstalling Ubuntu easier. A root partition of 10-15GB should be good for root. If you plan on installing lots of games and stuff, and since you have a lot of room, then you could make root larger as Fancypiper suggested. My Ubuntu root on my desktop is 14GB. My laptop has a 10GB root. Unless I have installed big games like Doom3 or Quake4 on my system, my Ubuntu root partition is never larger than about 3.5-4GB.
I also think 10GB for swap is too much. If you plan to use hibernate, then set swap to at least the size of the amount of memory you have.
> **underquark said:**
> 
I have just ordered a 1.5Tb drive to add to my system.
What will this be used for, Windows (NTFS) or linux (ext3 or ext4)? 
I have 2 hard drives on my system. The first is for operating systems (Windows + several linux distros). The second is for data.
> **underquark said:**
> 
For the moment I wish to continue using 9.04 but I want to upgrade to Lucid when it comes out.
Note that you may not be able to upgrade directly from 9.04 to 10.04. It is recommended that you upgrade in sequence (i.e., 9.04 > 9.10 > 10.04). I always do clean installs of Ubuntu myself.

---

### Post by raymondh on 2010-01-12
- 1hd for windows and its' bootloader in the MBR.  I would also dual boot this drive with win7 ... when the time comes.
- 1hd for Ubuntu and GRUB in it's MBR chainloading windows (XP or both).  This drive I would divide into swap, root and /home (in that order)... plus a spare partition for any experimental distro I want to try.
- 1hd for data storage to be accessed by both Ubuntu and windows.

Raymond

---

### Post by Bucky Ball on 2010-01-12
> **underquark said:**
> 
Drive 1:
Windows XP in about 300Gb partition - NTFS
ubuntu 9.04 64-bit in 600+Gb partition - ext3
10 Gb swap partition (I dream of getting hibernate to work one day)

Drive2:
1Tb NTFS containing data only (pictures, videos, music)


2Gb swap max, 10Gb pointless.
Put pictures, videos, music on separate partitions on the disc.
Use disc 3 for regular backups perhaps when the partitions on disc 2 are getting full or anything you don't want to lose.

---

### Post by oldfred on 2010-01-12
I agree with raymond. I like to have every hard drive have an operating system and that operating systems boot loader in the MBR of that drive. That way I can boot even if one drive has problems. 

If you are thinking about additional operating systems a separate /data partition is better than a separate /home as /home can only be used for Ubuntu but /data can be used everywhere and linked into home. I just changed to a separate /home based on all the recommendations with a new drive but also created /data and now my home is less than 1GB with 3-4 years of history still in it. All data is linked from the /data partition so home only has the system settings (mostly hidden).

Since you have a new drive you should install to the new drive but keep your old install until you decide you have nothing left to copy in the way of old settings. I only found one or two things I needed from the old install but it made it easy to go back and find them.

---

### Post by underquark on 2010-01-12
Thank all for your comments. I've taken from this the following:

Put /home on separate partition OR put /data on a separate partition (or both)
Different OS on each of two drives in case one becomes unbootable
Leave a partition for trying out different distro's
Sort out my swapfile
The big drive will probably get formatted ext3

Since I have two existing 1TB drives I'll try and cull >500Gb rubbish leaving space to back up everything to the new drive then maybe go for a clean install of ubuntu on one and XP on the other.  Don't need Win 7 for the small amount of Windows stuff that I do and I already have a copy of XP.  I might put any shared data on the Windows drive or set aside space here for stuff that I may want to work on in Windows prior to moving elsewhere (I like VideoReDo to process .REC files from my digital recorders, for instance, and I still have stuff I did using Google Sketchup).  Thank you all, once again.

---

### Post by tommcd on 2010-01-13
> **underquark said:**
> 
Put /home on separate partition OR put /data on a separate partition (or both)
Different OS on each of two drives in case one becomes unbootable
Leave a partition for trying out different distro's
I would also recommend using a /data partition if you plan on installing multiple linux distros. This is in fact what I do, since I have several distros on my system. The rationale for this is so all the hidden  files and directories that are kept in the home directory are kept separate for each distro, so they can't conflict with each other. On my system each distro's home directory is on it's root partition, and all distros share /data. Your first post only mentioned Ubuntu and Windows, so I just recommended a separate /home for simplicity. If you only have 1 linux distro there is no real advantage to a seperate /data partition as opposed to a separate /home partition.

Having Windows and linux on separate hard drives is an option that many people use. This allows you to preserve the Windows MBR on the Windows drive, and have grub on the MBR of the linux drive.
 I don't use Windows enough to justify devoting an entire hard drive for it though.
I like having my OSs on one drive and my /data on another drive. I will sometimes repartition the OS drive to make room for another distro, or delete or resize a partition depending on what I want to do. Having my data on a separate hard drive allows me to change the partitions on my OS drive all I want without fear of losing any data.

---

### Post by compaz1 on 2010-01-13
> **tommcd said:**
> I would also recommend using a /data partition if you plan on installing multiple linux distros. This is in fact what I do, since I have several distros on my system. The rationale for this is so all the hidden  files and directories that are kept in the home directory are kept separate for each distro, so they can't conflict with each other. On my system each distro's home directory is on it's root partition, and all distros share /data. Your first post only mentioned Ubuntu and Windows, so I just recommended a separate /home for simplicity. If you only have 1 linux distro there is no real advantage to a seperate /data partition as opposed to a separate /home partition.

Having Windows and linux on separate hard drives is an option that many people use. This allows you to preserve the Windows MBR on the Windows drive, and have grub on the MBR of the linux drive.
 I don't use Windows enough to justify devoting an entire hard drive for it though.
I like having my OSs on one drive and my /data on another drive. I will sometimes repartition the OS drive to make room for another distro, or delete or resize a partition depending on what I want to do. Having my data on a separate hard drive allows me to change the partitions on my OS drive all I want without fear of losing any data.

I am a lurker, but I like the idea of the data on a separate drive from the OSs.

---

### Post by tommcd on 2010-01-13
> **compaz1 said:**
> I am a lurker, but I like the idea of the data on a separate drive from the OSs.
Well, welcome to the Ubuntu forums!
But don't just lurk... participate! This is a great forum.

There are many ways to partition hard drives for dual booting Windows plus one or more linux distros. There is no one "right" way. It all depends on your particular hardware setup and what your needs are for operating systems, partition sizes, etc.

Just out of curiosity, what is your partition setup?

---

### Post by Bucky Ball on 2010-01-13
Data on separate drive from OS absolutely, but drive for each OS is a waste of space , as they say! :)

---

### Post by underquark on 2010-01-13
Look, even my large swap partition is only taking up 0.3% of my space so I'm smugly not worried.  I fitted the 3rd drive today - it's a Samsung Ecogreen F2 1.5Tb.  Slow spin (5400) but it's only going to be used as a data bucket and I've always been happy with Samsung drives in PCs, PVRs etc.  I stuck in a new 12cm fan while I was at it.

---

