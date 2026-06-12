---
title: "Fixing Grub"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by Seeker84 on 2007-09-21
So here's my take on the reinstall Grub Topic.

First this is my system.  one IDE with two partitions both NTFS but only one has Windows XP on it.
One SATA drive with Ubuntu Feisty Fawn (Ubuntu Ultimate 1.4), a swap partition and a whole lot of free space.

My problem was that grub was loading to slow, so I decided to move the WinXP to the free space on the SATA.  I installed XP successfully on the free space on the SATA drive.  This was in hopes to speed up grub.  

I go my trusty WINXP CD out and booted from it.  I got into Recovery mode and then selected my main windows partition on my IDE (it only showed me those, I'm wondering it I booted to my SATA it would only show me one) and then typed in "fixmbr"  this then warned me that there is a risk but I accepted the risk and fixed the MBR.

At this point, grub will not work, if I have either drive as a master, I'll get Windows XP, SATA will have the clean XP show up and the IDE will have my wondows XP show up.

then I used the Live CD to start into Ubuntu.  From here I opened terminal, go to "sudo -s", a MUST if you want to do this next step.  I then typed in grub, it then gives you the grub prompt.  Please read the top portion, like the part where it says tab if you don't know what to type in, it's very helpful.  I then found where the /boot/grub/stage1 was, I used this in the next parts.  I then did the absolute command, normally just the first part of this would be sufficient but in my case I went with the absolute.  "install (hd1,0)/boot/grub/stage1 d (hd0) (hd1,0)/boot/grub/stage2 p (hd1,0)/grub/menu.lst" (I found this somewhere out there, it may be buried int he grub manual, but I didn't save the link of where I got this from.)

All that command did was restore what I already had on my system.  But  My main goal was to get grub going faster, and HEY it worked.  So I don't need to migrate information from one partition to the other for XP.

If this helps you I'm glad I could help you along. :-D

---

