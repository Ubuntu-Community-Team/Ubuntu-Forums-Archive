---
title: "Mutli Boot Install trouble"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by KLund1 on 2012-10-31
I am having some trouble install Ubantu on an empty partition on a multi boot system.
Here is a my drive layout from win7's view point. See pic 1 

I want to install Ubantu in the empty section at the end of Disk1. But the Ubantu installer does not see any of the partitions on Disk 1, see here. It is /dev/sdg (sorry about the big picture size) See pic 2

I can not add to /sdg, or change it. I can put a new partition table, or format it. But that would wipe out the other OS's installed there.  If I just click INSTALL I get a warning about "No root file system" "Please correct this from the partition menu"

Some system info that is reliant. I multi boot win7 from a PCI SSD, and then Win7, Vista, and XP from the same HD. (win8 in not installed yet, but made space available when I do.) The large drives are back up & data only.
Suggestions on how to proceed with my unbantu install. Or let me know if I need to clarify something.
Many thanks.

---

### Post by Tranas on 2012-10-31
> **KLund1 said:**
> I am having some trouble install Ubantu on an empty partition on a multi boot system.
Here is a my drive layout from win7's view point. See pic 1 

I want to install Ubantu in the empty section at the end of Disk1. But the Ubantu installer does not see any of the partitions on Disk 1, see here. It is /dev/sdg (sorry about the big picture size) See pic 2

I can not add to /sdg, or change it. I can put a new partition table, or format it. But that would wipe out the other OS's installed there.  If I just click INSTALL I get a warning about "No root file system" "Please correct this from the partition menu"

Some system info that is reliant. I multi boot win7 from a PCI SSD, and then Win7, Vista, and XP from the same HD. (win8 in not installed yet, but made space available when I do.) The large drives are back up & data only.
Suggestions on how to proceed with my unbantu install. Or let me know if I need to clarify something.
Many thanks.

Your issue appears to be related to raid. The resident guru on this is Darko [search for his threads mentioning raid] - hopefully he will offer to help. 

My guess is that Ubuntu sees no partitions because the drive is flagged as being [having been part of a] raid, however your issue is way beyond my comfort level. 

A major failure in Ubuntu is that when it sees that flag, it simply sticks it's head in the sand and essentially kills the install process or gives you a choice [bad] to destroy your existing configuration. Tread lightly. HTH

---

### Post by KLund1 on 2012-10-31
Thanks for the quick reply. Lot of good threads from that user!!!
But did something often unheard of..... Goto the Ubuntu home page!!! What did  I find?
A Ubuntu, windows installer!!!! Just formatted the un-partitioned space, gave it a letter, ran the installer, and BOOM!!! got Ubuntu installed and it also added a item to my boot-manger OS list!!!!!!!! No dealing with grub, or BCE in windows!!!!
It really could not be easier!!! 
I bypassed the 'donation' page on the original download of the windows installer. It went so well. I went back and added more to the donation !!!!! well worth that nominal fee. 
NOt sure whom to thank in lunix-land, but more than thanks is due.
That installer should have TV ad's after each win8 ad.!!!!!!!!!!!!!!!

I'm good this issue is closed for good. :KS:KS:KS:KS:):):):)

---

### Post by Tranas on 2012-10-31
> **KLund1 said:**
> 
But did something often unheard of..... Goto the Ubuntu home page!!! What did  I find?
A Ubuntu, windows installer!!!! Just formatted the un-partitioned space, gave it a letter, ran the installer, and BOOM!!! got Ubuntu installed and it also added a item to my boot-manger OS list!!!!!!!! No dealing with grub, or BCE in windows!!!!
It really could not be easier!!! 

Although you are apparently satisfied at this point, I would hasten to add that the issue with raid was not resolved with the wubi install. If I understand correctly, what you have now is essentially the live-CD installed on your hard drive. Be sure you have a backup of your data before trusting such a configuration with your data - ymmv.

---

### Post by oldfred on 2012-10-31
wubi is a good way to have an extended test of Ubuntu, but it is inside your NTFS partition and uses the Windows boot loader, so it is not a full partitioned install.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
> Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


Since you have multiple drives, my suggestion eventually is to have Windows on one drive & Ubuntu on another. I prefer to have an operating system on every drive and to make sure it will boot from that drive without any of the others. So when (not if) one drive fails I can boot the other drive.

---

### Post by KLund1 on 2012-10-31
I understand about the RAID issue. But that is just WIn7 Boot drive, and Ubuntu does not need to have access to it. I do not need linix to be a full partitioned install. I live-CD version on my HD is just fine for now. I just wanted it be in it's own corner of my fasted spinning drive.  And that it loads from a windows bootloader is just a great added bonus.  AS you suggest, I may do a real install on a separate drive in the future.
Many thanks for your input, Most helpful. Getting quick help on subjects like this from others is what makes open source the way of the future!!
Take care

---

