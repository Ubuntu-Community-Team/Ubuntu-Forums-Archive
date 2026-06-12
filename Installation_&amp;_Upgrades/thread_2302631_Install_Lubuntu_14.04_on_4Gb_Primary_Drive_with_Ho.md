---
title: "Install Lubuntu 14.04 on 4Gb Primary Drive with Home folder on 8Gb Storage Drive"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by West Swan on 2015-11-11
Hello,

I have an old eeePC which has a 4Gb 'fast' Primary hard drive and a second 8Gb 'slow' drive for storage.

I have successfully installed Lubuntu onto the 4Gb drive with the ext2 file format and with no Swap File.  Even with all the updates I still only used just over 3Gb of the 4Gb drive.

Then tried to move the home folder to the 8Gb using lots of command line stuff which I hate and which totally screwed up my system :-)

I have already used Gparted to remove all partitions from the eeePC and now want to clean install Lubuntu again using the same settings as before but putting the home folder onto the 8Gb drive right from the start.  I will format the 8Gb drive as ext2 as well.

Is that a simple thing to do?  I found someone had done this in an old Ubuntu but I couldn't make sense of it.

Hope this makes sense.

Regards,

Paul

---

### Post by Bucky Ball on 2015-11-11
During install choose 'Something Else' and you can assign the 8Gb as /home and the installer will do the rest for you. It will create the /home partition at that mount point and include your settings and default /home folders, /Documents, Music, etc. There is no need to install Lubuntu then move the /home folder to its own partition. Redundant.

I'd say go again if this is a fresh install, choose Something Else at the partitioning section of the install, create a 4Gb for / and give it the mountpoint / and an 8Gb partition for /home and give it the mountpoint /home. Those mountpoints are selectable as defaults in there. Easy. :) (PS: There are a [ton of how-tos]("https://duckduckgo.com/?q=Ubuntu+create+separate+home+partition+during+install") online about how you do this.)

[This]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") may also help. 

Why ext2? That is old. Very. EXT4 is standard now. Unless you have a specific reason for ext2 ... :-k

---

### Post by West Swan on 2015-11-12
Hi Bucky Ball,

That is awesome thank you :-)

Re EXT2.  Somebody I read elsewhere on this forum that as it doesn't support journaling the SSDs will last longer than if  Ext4 (or Ext3) was used.

If that is incorrect I am happy to go with EXT4  

Regards,

Paul

---

### Post by ubfan1 on 2015-11-12
You can turn journaling off with ext4, but since these days, the ext4 driver is used for ext2 (I think), there's not much difference.

---

### Post by Bucky Ball on 2015-11-12
> **ubfan1 said:**
> You can turn journaling off with ext4, but since these days, the ext4 driver is used for ext2 (I think), there's not much difference.

In fact, if you turn journalling off you have EXT2. Yes. EXT4 is common on SSDs now, but they are new than what you have probably. You are saying you have a 12Gb SSD? Or is it an eMMC?

---

### Post by West Swan on 2015-11-12
Hi again,

It is a 4Gb SSD plus another 8Gb SSD I think in the eeePC 4G

I have just installed as per your instructions and it is perfect.  The 4Gb drive has 1.5Gb free space now that I have moved the home folder to the 8Gb drive.

Awesome :-)

---

### Post by Bucky Ball on 2015-11-13
Great work. You could create a 1Gb or 1.5Gb /swap there. Just let us know if you can't work out how (easy enough to use Gparted> Right click free space> make is 'swapspace'. The trick is in writing it into the fstab so it boots and is on when you boot your computer. :)

---

