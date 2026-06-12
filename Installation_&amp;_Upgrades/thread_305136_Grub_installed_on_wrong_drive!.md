---
title: "Grub installed on wrong drive!"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by Danathar on 2006-11-22
I just installed 6.10 for the first time. 

I have two drives, one with WinXP the other was empty. When I went to install Ubuntu it installed Grub as the bootloader on the primary drive! Which is NOT what I wanted to do. I wanted to keep them both seperate because my BIOS supports booting from different drives.

I'm not dead in the water, but I want to get rid of Grub on on my WinXP drive , install it on the MBR of the Ubuntu drive. Then I can boot either OS via my bios.

So step 1 should be to install grub on the MBR of the ubuntu drive which is /dev/hdd. How can I do this? There seems to be no grub.conf anywhere?

After testing it, then I need to get rid of grub from the MBR of the WinXP disk (/dev/hda) and restore the Windows MBR.

I'm kinda pissed. Had I known it was going to do this I would of pulled the power from my WinXP drive prior to installation.

Thanks for any help in advance!

---

### Post by Bartender on 2006-11-22
Danathar - 
As long as you have or can borrow a Windows XP CD, repairing the MBR is relatively painless.  Elder Geek, Kelly's Corner, etc. have guides.

As for the other drive, just reinstall Ubuntu.  On that last page, after the partitioning part, look for the little box describing where GRUB will go.  You want "hd1" if the Windows drive is still plugged in.  GRUB numbers drives differently than Linux.  Linux starts with "1", GRUB starts with "0".  So in the GRUB universe your Windows drive will be "hd0", the second drive will be "hd1".

Or fix GRUB.  I'm not familiar with that process, but lots of guides for that too.

---

### Post by confused57 on 2006-11-23
Ubuntu uses /boot/grub/menu.lst(short for list) instead of /boot/grub/grub.conf.

You can restore your Windows mbr using this link:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You can reinstall grub to your Ubuntu drive, using the desktop live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Here's how I have my system setup with 2 drives:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

The desktop live cd doesn't give you the option of where to install grub...the alternate install cd does allow you to select which partition or drive mbr.

---

