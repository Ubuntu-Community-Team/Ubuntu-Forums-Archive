---
title: "Grub problems...."
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by stingerssx on 2007-09-01
So, let's say that I have a 60gig primary drive loaded with Windows.

   And I have a blank 120gig. I want to dual boot, but there isn't enough room on the 60gig to add Ubuntu. So I install the 120gig into the master of the secondary drive, make 2 60gig partitions, ghost Windows to the first 60gigs, and the install Fiesty on the second 60gigs. With the primary master still the original 60gig HDD. I want to remove the original HDD, and put the 120gig into the master of the primary. When I do, grub doesn't load. 

    Now, under Windows (original 60gig HDD)  I can see and access both the original HDD with Windows, and the ghosted partition. I can see the Fiesty partition, but Windows says it's an unknown partition (what else is new?). Also I can boot into Fiesty with Grub, and from there I can access one Windows drive. (I don't know which one though)

    How can I fix this? I'm under the impression that the Windows boot loader knows to boot from Grub, but when the Fiesty partition goes from HDB2 to HDA2, Grub freaks out and gets lost. I have checked boot.ini from both Windows partitions, and both seem to be correct. Also, niether even mention grub, or using another boot loader. I would rather not reload Fiesty. I'm thinking the only thing to do is fix the MBR with the CD, then put the 120gig into the primary master, then using the Ubuntu live CD, navigate to Grub. Is this possible? Is there some other way of doing it? Any thoughts?

---

### Post by Herman on 2007-09-01
Hello stingerssx,
I think probably you just need to install GRUB to MBR in your new hard disk, here is a link about how to do that, [                                                                  Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") eg; with Live CD.
Your Windows boot loader will never recognize any other OS and set itself up automatically, but your Ubuntu boot loader, GRUB, can do that most of the time. However, since you have changed the way your hard disks were plugged in, you will need to make ammendments to it manually.

You will need to edit your /boot/grub/menu.lst file in Ubuntu. 
Ubuntu will have settings telling it that it's in a second hard disk but now it's in a first hard disk. Here is another link about how to [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") and rescue your Linux system with a Live CD. That link will tell you how to open your menu.lst file so you can edit it. You might also want to edit your /etc/fstab file too.

Actually, if this is a new Ubuntu installation, (no important files and settings in there to worry about yet), and if you are a new user, it would be quicker and simpler to just re-install Ubuntu. That will only take half an hour, and the Ubuntu installer will set everything up correctly for you automatically for the hard disk and partition arrangement you have now, and will set GRUB up to chainload your Windows bootsector and boot Windows for you. That would be the easiest and fastest way, and that should fix all your problems.

Otherwise if you have questions you will be able to get help here in Ubuntu Web Forums to edit those files manually with the Ubuntu Live CD, but you will need to post copies of those file here and also the output from the command:sudo fdisk -lu from the LiveCD,
```
sudo fdisk -lu
```Regards, Herman :)

---

