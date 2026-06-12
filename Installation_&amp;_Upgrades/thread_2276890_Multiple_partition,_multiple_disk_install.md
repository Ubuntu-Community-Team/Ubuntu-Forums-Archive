---
title: "Multiple partition, multiple disk install"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by pmi2 on 2015-05-05
My question is about this "Example Partitioning Scheme" from the official Ubuntu Help pages:

[https://help.ubuntu.com/community/DualBoot/Partitions#Example_Partitioning_Scheme](https://help.ubuntu.com/community/DualBoot/Partitions#Example_Partitioning_Scheme)

Basically need some info on two points, 1) the suggestion to use both ext3 and ext4 partitions, and 2) the suggestion to use separate /home and swap partitions on a second drive.  The same help page also suggests > If you dual-boot or multi-boot with another linux distro then the swap and /home can be shared by them 
I ask because I am in the process of rescuing/repairing an older, but moderately fast laptop (HP EliteBook 8560), which can accommodate older mSATA SSD in addition to a conventional hard drive, as well as external eSATA, so it seems like a perfect test for some kind of multiple partition, multiple hard drive setup.

Btw, I did check that both Windows and Ubuntu 14.04 install and recognize all the peripherals and other hardware in the case, but that is as far as I have gone, default installation only.

Thanks in advance.

---

### Post by sandyd on 2015-05-05
My recomendation, assuming your installing Windows/Linux:
 - Place the OSes on the SSD
 - Place the Swap/Home partition on the HDD
 - Use eSATA as backup drive.

Side note: You may choose to place one OS on the SSD if it doesn't have enough space.

Side note #2: Generally, filesystem does not really matter, I generally use ext4 for general purpose, and JFS for smaller files.

---

### Post by pmi2 on 2015-05-06
> **sandyd said:**
> ...Side note #2: Generally, filesystem does not really matter, I generally use ext4 for general purpose, and JFS for smaller files.Thanks for the reply.  I was curious why ext3 AND ext4 was recommended on that help page.  So far, when I have installed recent versions, it always defaulted to ext4.

I will probably use the eSATA port for a second data drive, if one is ever necessary, my external backup is USB3, and I can't easily change that b/c of other systems I am backing up.  It is fast enough for my purposes.

---

### Post by oldfred on 2015-05-06
Your link is older and does have an error or two.
You cannot share /home with Windows. /home has to have Linux format, and Windows only reads NTFS or FAT32.
While you can share /home and swap with other Linux, some have issues.
If you share swap you cannot hibernate, but normally when dual booting hibernation is not suggested anyway.
Some have had good success sharing /home others not. Depends on what each system writes for your own configuration settings into /home. If user settings are totally different then usually not an issue. And if settings are totally identical why a second install? 
I suggest and use a shared data partition, and only /home user settings which are a very small part of /home stays in /home.

---

### Post by pmi2 on 2015-05-06
> **oldfred said:**
> ...I suggest and use a shared data partition, and only /home user settings which are a very small part of /home stays in /home.Thanks, I have that same configuration on my desktop now, and it works well for me.  I cannot duplicate my desktop setup on this laptop, not w/o spending more $, but I do have enough older spare parts to get it back into productive use with some combination of small-ish SSD and older SATA II disks, and using a USB 3 drive for any overflow data storage (videos, my simulations etc.)

I was curious about that particular help page, and the suggestions there, and it is difficult to know what is actually recommended by the team here.  Both ubuntu 14.04 and Windows 7 SP1 load and run fine in default configuration, and without any manual tweaks or extra driver install, the Radeon 6470M is recognized fine, and I seem to have both WiFi and Ethernet, but that is as far as much as I have had time for so far, therefore, my q. about the recommended partitions, :D

---

### Post by grahammechanical on 2015-05-06
That wiki page is part of the Community wiki. I am not saying that the persons who write those wiki pages do not know what they are talking about but it is just that even I can edit community wiki pages! Keeping these pages up to date requires volunteers to do the editing.

As far as I know the main difference between Ext3 and Ext4 is that Ext4 uses Extents instead of the block mapping of Ext3.

> An extent is a range of contiguous physical blocks, improving large file performance and reducing fragmentation.

[http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

There was a time when Ext3 was the default file system and Ext4 was experimental. I can remember stories in computer magazines about possible loss of data when using Ext4. Even when Ext4 became default in Ubuntu I still kept my data partition as Ext3 just to be on the safe side.

At the time that wiki page was written it might have made sense to put the OS on Ext3 as there was less risk of fragmentation. I imagine that there are lots of reads from the OS but very few writes to it. Whereas, the partition with user data on it would be more at risk of fragmentation due to the editing of documents.

As for a partition that is set aside for experimental installs of Linux it hardly matters whether is it Ext3 or Ext4. Data will not be kept on it and the file system will be formatted with every new install.

If we put in another installation of Ubuntu then the installer will automatically detect the existing swap partition and make use it.

Regards.

---

### Post by pmi2 on 2015-05-07
Thanks for the clarification.  Perhaps that page needs editing again, especially if this is the default help page for dual or multiple partitions.  

Both of the first two Ubuntu Help pages that come up in a search seem somewhat different from the typical multiple OS installations discussed in this forum.  Neither one corresponds to what you get if you simply allow first Windows, and then Ubuntu to install with default settings.  

Or for that matter, what to do if you add an SSD to a system with a hard disk (this must be fairly common now, b/c of the dropping price of SSDs).

---

### Post by SeijiSensei on 2015-05-07
I routinely use ext2 to format any /boot partitions I might use.  The filesystem is so small that it doesn't take long to run fsck if needed without the journalling in ext3/4, and this avoids any issues about whether there is support for ext3/4 in initrd.  That was a common issue some years' back.

Windows can read ext3/4 partitions with this driver: [http://www.ext2fsd.com/](http://www.ext2fsd.com/).  Until recently it did not work with ext4 systems and even now has some limitations with that format.  Works well with ext3 though as I recall.

---

### Post by pmi2 on 2015-05-07
> **SeijiSensei said:**
> Windows can read ext3/4 partitions with this driver: [http://www.ext2fsd.com/](http://www.ext2fsd.com/).  Until recently it did not work with ext4 systems and even now has some limitations with that format.  Works well with ext3 though as I recall.Interesting, thanks, I will look into that.  Until now I have only shared data between Windows and Linux using Ntfs volumes.

---

