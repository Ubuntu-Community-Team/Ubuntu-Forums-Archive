---
title: "Ubuntu doesn't recognize RAID array on SB600 controller"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by NateLowrie on 2008-06-03
I just built a new computer and want to dual boot Windows and Ubuntu.  I have 4 Hitachi drives connected to the sata controller in the SB600 Southbridge chip in my mother board.  The drives are setup in a 10 RAID array.  The Raid array has one 160 Gb NTFS file system on it and 160 Gb of non-partitioned space which I want to partition to install Ubuntu on.  I boot into the Kubuntu CD and proceed to install the OS.  When I get to the screen for choosing a partition to install on, I see the 4 individual drives instead of the partitions on the array.  I don't have a choice but to select one of those 4 drives.  I don't want to go any further till I know I won't blow away my windows install.  What do I need to do to see the array?

Every Google search I have done on this refers to posts about sound or graphics issues.  I couldn't find any forum posts about this either.  Am I just not going far enough in the install?

Thanks.

Nate

---

### Post by dhscaresme on 2008-06-07
This has happened to me as well, however I'm on an evga nVidia 650i ultra mobo. 

I've been told the RAID is not very good w/ this chipset. So, NateLowrie, you've got one more person on the case.  I'll let you know if something turns up. 

I've set up two separate arrays (each w/ two SATA discs) and I always see 4 discs in the installer.  This happens no matter how the RAIDs are set up: as one big RAID 0, or RAID 1, or whatever. The installer will just install to which ever disc you pick.  

This is not just a problem with the installer application as the LiveCD reveals the 4 drives individually (/dev/sda..d).  They're mountable and I can r+w the file systems.  

Another note:  I had 8.04 installed a few days ago w/ my discs set up like this:
2x500gb RAID 1.
1x 160gb, no RAID.
1x 120gb, no RAID.
I was running 8.04 just fine, but like the LiveCD, I was able to mount each of the 500gb drives individually and use the discs. This installation was on the 160gb drive. After a few days I removed the RAID 1 and, oops, I guess the MBR was on it because now I can't boot. 

How in the ubuntu installer can I spec. which drive to install the MBR on? Or am I not understanding something?

I'm wondering about drivers, I just haven't gotten very far along in researching this yet. 

This is not a dual boot machine either.

--dh

---

### Post by dhscaresme on 2008-06-08
Okay my problem was that I don't have a truly hardware based RAID, it's FakeRAID.  So I'm just gonna software RAID the big drives for backup.

--dh

---

### Post by delete2end on 2008-06-12
I have an Asus board with the SB600 raid....is there any way that I can install Ubuntu 64 on a RAID 0?

it will not recognize the raid driver CD I put in....

Another question is can I add the raid driver from ASUS to the ISO image and then burn to cd for install?  I currently use Alcohol 120 to manage my ISO's.

Please help as I am tired of Windows

James Irish
[email]delete2end@gmail.com[/email]

---

### Post by arpanaut on 2008-06-13
This thread might get you started in the right direction:

[http://ubuntuforums.org/showthread.php?t=630644&highlight=fake-raid+howto](http://ubuntuforums.org/showthread.php?t=630644&highlight=fake-raid+howto)

another one:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

