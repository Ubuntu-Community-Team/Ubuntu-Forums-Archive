---
title: "Does Partition Magic Work with Ubuntu?"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Zenguy on 2007-02-05
Is there a simple answer to this question: “Does Partition Magic Work with Ubuntu?” 

It seems that the Ubuntu installer will corrupt existing Partition Magic partitions during the installation. (There have been several posts about this.)

I am considering blowing away all partitions, doing a fresh Ubuntu install, then use Partition Magic to setup the remaining XP partitions, but I was wondering if anyone has tried doing this with success. Taking a Linux first, Partition Magic second approach may solve this problem, but I was wondering if anyone had input on this.

If not, is there any other surefire way that I can get Ubuntu and Partition Magic to coexist peacefully?

Some stray facts:

The maker of Partition Magic (Symantec) does not have any support information on their site regarding Ubuntu.

I have several partitions on my primary hard drive. 2 x NTFS Bootable, 1 FAT32 Data and whatever Linux wants to setup. I also have a gaggle of external drives that are waiting patiently in the wings until I figure this mess out.

I am very well versed in Windows, software testing and low level utilities, but my Linux experience is only several days old. (In other words, I may not “grep” what you are saying if you get too Linuxy on me.)

Thanks.

---

### Post by davidcrickett on 2007-02-05
I have used Partition Magic 8 to partition before installing Breezy Badger, and it worked out fine, but I don't know with edgy...

---

### Post by loserboy on 2007-02-05
I used it with dapper, seemed to work fine

---

### Post by Zenguy on 2007-02-05
davidcrickett - Could you list the partitions that you set up using Partition Magic and their sizes and order that they exist on the hard drive? Also, your install was for hard drive 0, right?

Here are more details of my recent flirtation with partition disaster.

Last night I tried to the following without success:

1) Blew away all partitions from my primary hard drive.
2) Created the two NTFS Primary partitions.
3) Created the FAT32 data partition within an extended partition.
4) Used Partition Magic to create the swap and home partitions for Linux
5) Ran the Ubuntu install and told it to use the partitions that I created for it.

Result: Partition Magic says the hard drive is corrupt. The drive seems to dual boot properly, but the warning message from Partition Magic reports are pretty scary. I don't know if it will lead to data corruption in the long term.

I suspect that this may have to do with the fact that either the Ubuntu installer is pushing past the magical 4 partition boundary that Windows is sensitive to. Or else Ubuntu may be modifying the partition tables in such a way that Partition Magic gets confused. That's why I was thinking of doing the Ubuntu install first, then use Partition Magic to do the complicated partitions after that. 

With the release of Vista, I suspect there will be a surge of new interest in Linux.

---

### Post by etank on 2007-02-05
I have used Partition Magic many times in the past with success. I have recently switched to using gParted though and it works great. Had to use it recently to save a Windows box that had a 4Gig C drive and was running Windows 2003. It can be uses as a live CD as well and can be found at [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/). Best of all its free.

---

### Post by dbqp on 2007-02-05
> **etank said:**
> I have used Partition Magic many times in the past with success. I have recently switched to using gParted though and it works great. Had to use it recently to save a Windows box that had a 4Gig C drive and was running Windows 2003. It can be uses as a live CD as well and can be found at [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/). Best of all its free.

I completely agree! GParted was used this past weekend to shrink my Windows partition and resize my /home folder.  I also created a new partition.

Use the GParted Live CD (version 0.3.3) for best results, as you don't have drives mounted and other worries to contend with!

Good Luck!

---

### Post by Zenguy on 2007-02-05
Well these success stories are somewhat comforting, but I still can’t isolate what I’m doing wrong.

I was using Dapper to do the installs.

Partition Magic version 8.01

I setup Linux Ext2 partitions, not Ext3.

I actually did the installation twice. The first time I just told Ubuntu to claim about 20 GB of unused space. In the second attempt I had setup the partitions with Partition Magic as outlined above then assigned Linux swap and home areas to them.

I’m skittish about using GParted for the same reason that Partition Magic is reporting these errors. Since Partition Magic is Windows centric, it is probably more sensitive to scenarios that may corrupt a Windows environment. As a diagnostic tool, Partition Magic is telling me that something is wrong with the partitions, and I take that pretty seriously. (In all fairness it could just be a bug in Partition Magic.)

GParted appears less Windows centric and possibly less prone to identifying windows issues, but I’m only guessing here. I will consider it if there is no way to get this to work. I have a history with Partition Magic, so it’s really more of a trust thing.

---

### Post by Greg Knight on 2007-02-05
I just discovered gParted last night and I could only sing it's praises.

I'm dual booting XP and edgy; and have a single 160GB drive that was partitioned as:
[LIST]
[*]20GB NTFS (WinXP)
[*]and a logical partition broken down as:
[LIST]
[*]70GB FAT32 (Data)
[*]2GB Swap
[*]10GB EXT3 (/)
[*]58GB EXT3 (/HOME)
[/LIST]
[/LIST]

I needed to move 20GB from the FAT32 to the NTFS and gParted was quite accommodating.  It shrunk the FAT32 and the entire logical partition and then grew the NTFS partition.  The only thing I did was defrag both drives afterward.

Next chance I get I'm going to use it to move some of the free space in my /HOME all the way back to the FAT32 partition.

I was always scared of using partitioning tools on a live system, but not now!

---

### Post by Zenguy on 2007-02-08
I’ve had some success and I thought I would share my experience in the hopes that it helps someone else.

Yesterday I backed up my primary hard drive (0) and started playing around with partition software. Everything was working fine with XP, so I cranked up the Ubuntu Edgy installer. Sure enough, as soon as Ubuntu completed its installation, Partition Magic was reporting an LBA and CHS mismatch which it wanted to correct. Regardless of whether it corrected them or not, Partition Magic reported that the drive was “Bad.” Worse yet, the Ubuntu installed partition software QTParted couldn’t see it properly either.

The drive appeared to boot correctly, but if I left it in this state I would have to say goodbye to any future partition manipulations.

I tried several other things, but the conclusion that I came to was that if Partition Magic originally created the partitions, then the Ubuntu install was going to corrupt them. Other folks may not have this experience, but I tried just about every different combination. 

Then I wiped out all of the partitions.

I used the utility that was mentioned in a previous post, GParted, and created the partitions from scratch. Then I woke up Partition Magic and tested to see if it could read the disk. Partition Magic gave me a minor error about my extended partition being labeled as “Extended” and not “ExtendedX.”  It corrected this issue and now all of my partition software sees the drive without any errors.

I currently have the drive partitioned like this:

NTFS Primary 70 GB (XP 1)
NTFS Primary 15 GB (XP 2)
EXT3 Primary 40 GB (Linux primary)

Extended Partition
----
SWAP 1 GB (Linux swap)
EXT3 10 GB (/home)
FAT32 10 GBData
FAT32 10 GB Data

Over the next few weeks I will probably make more changes to the structure as I figure out what Linux wants and where it wants it.

For my money, GParted is a better utility than QTParted. When I was experimenting with the drive, it was the only utility that could see the partitions when the other utilities just saw one big “bad” block.

One note of caution. I had problems with my backup image and had to pull portions from a previous backup. Make sure you verify your backups before you go down this path.

---

### Post by mike_f on 2007-02-19
I too was pleased to discover the gparted standalone boot iso (!). I proceeded with caution and tried it on my secondary system and, like the above poster, Partition Magic v7 will No Longer recognize the partitions.
I've tried to resolve this issue with the well regarded 'testdisk' utility to no avail - I don't know what to think at this time. It seems like testdisk, gparted and Partition Magic can't agree on which CHS disk geometry is 'correct' or 'best'. 
Given how little PM has been upgraded recently (AFAIK NONE since the acquisition by Symantec in 2003) I'm not sure that PM really understands LBA. BTW I'm a ten year user of PM since version 3. Version 8 supposedly understands ext3 but still retains the shaky MSDOS underpinnings; if gparted doesn't work out I may try out Acronis Disk Director (experience, anyone?).
BTW the ptedit and partinfo utilities that come with PM seem to work under FreeDOS, be sure to look at them also.
TIA, Mike

---

