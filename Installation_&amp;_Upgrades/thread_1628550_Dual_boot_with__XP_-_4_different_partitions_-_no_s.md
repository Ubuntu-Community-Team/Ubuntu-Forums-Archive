---
title: "Dual boot with  XP - 4 different partitions - no success intalling Ubuntu 10.10"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by lcmp on 2010-11-22
For the past 4 days I´ve been trying to install ubuntu 10.10 64bit with no success.  I am a total newbee when it comes to linux so I will be needing your kind help with it. 



  At first I installed ubuntu to one of my portable drives with no problems, but now I want to install it to my hard drive and have a dual boot between windows XP and Ubuntu. 



When I arrive to the manual partitioning part is where I get lost. I have totally destroyed my windows installation 5 times already ( thank god for norton ghost for restoring my windows installation. )
  

I have read several articles and blog posts regarding a dual boot system with windows and Ubuntu but none of them cover my specific situation so I keep getting lost and screwing things up.


  I have 2 internal hard drives in my system.
  

1. A 750 GB drive for system and files.
  

2. A 1 TB drive just for files and backups of the first drive.
  

I have the 750 GB system drive partitioned the following way:
  

1. Primary partition:
  

- 50 GB for windows XP (NTFS)
  

2. Extended partition:
  

- 50 GB logical drive ( unformatted ) ( this is where I intend to install Ubuntu )
  

- 5 GB logical drive (NTFS) ( this is where I have the windows page file none of the other drives have a page file )
  

- 645 GB logical drive (NTFS) For files
  

OK. So I start the computer with the Ubuntu install CD. I get to where i´m asked if I want to run Ubuntu alongside other operating systems, I say yes. Then I realize that the slider thing is not gonna work for me because it will probably get rid of the other 2 logical drives I have set up. 



I notice there´s a link which says:
  

3 smaller partitions have been detected. Set partitions manually to have more control. ( more or less )
  

I click this link and get sent to the manual partition set up. This is where I have destroyed windows 5 times already jajaja..
  

I understand how Ubuntu recognizes my drives and partitions:
  
sda ( drive 1 ) sda1, sda2, sda3, sda4 ( primary and logical drives)
  

sdb ( drive 2 )
  

What I don’t understand and haven’t been succesfull is how to make the installer install all files into the 50 GB logical drive I have set up for Ubuntu.
  

I select the sda2 unformated free space but the installer tells me no boot option has been set up. 



Then I go to the options and there are a lot of different partitions being offered to be set up like:
  

/boot
  /swap
  /home
  /dev
  /user
  /temp
  And several more.
  

I understand that I need a /boot ,  /swap and /home, but what about the other partitions being offered to be set up? How big should each partition be? What file systems should I set up for each one?


  To anyone who tries to help me, Thanx in advance! :D

---

### Post by oldfred on 2010-11-22
The default desktop install is just / (root) & swap. You do not want the other system folders as partitions as it complicated things and makes it a lot more difficult to repair. Servers, RAID, LVM, & very old systems that have a BIOS boot limit of 137GB may need a separate /boot.

Basically take your 50GB of space and partition this way:
Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

Use gparted from the liveCD or a download of the gparted liveCD to create the partitions in advance adn then use manual install. You will tell the install which partition and what format to use for / & /home. If you defined a partition as swap it will automatically find it.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)

---

### Post by lcmp on 2010-11-23
Thank you very much for your help oldfred!!

You did point in the right direction.

It ended up being a lot of work in figuring things out and trial and error, but i eventually was successful.

I ended up doing the partitions manually with the liveCD of Gparted installed on a USB stck.

Then the Ubuntu 10.10 64bit installer run from a CDR-W hanged several times and crashed several times as well. I ended up putting the installer in a USB stick too.

It's all good now and i'm writing this reply from Ubuntu!!

Grub is working fine and my windows installation remains untouched and working.

Hopefully i will be able to get rid of windows for ever very soon.

Thanx again for your help.

cheers! :D

---

