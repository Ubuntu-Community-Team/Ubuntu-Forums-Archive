---
title: "Need to uninstall Ubuntu and merge partitons back together"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by whitewolf1218 on 2008-05-04
Hello, I have a laptop dual-booting XP and Ubuntu 8.04. I need to uninstall Ubuntu and merge its partition back with the XP partition to make the HDD one partition again, and I've been looking for the past hour and a half about how to do it and everything looks real confusing. I want to then reinstall Ubuntu using Wubi, but I can handle that.

I just need help getting rid of Ubuntu and merging the partitions back together. I'll need fairly detailed steps, while I'm not new to computers, I'm not a whiz either. 

Thanks in advance!

---

### Post by overdrank on 2008-05-04
> **whitewolf1218 said:**
> Hello, I have a laptop dual-booting XP and Ubuntu 8.04. I need to uninstall Ubuntu and merge its partition back with the XP partition to make the HDD one partition again, and I've been looking for the past hour and a half about how to do it and everything looks real confusing. I want to then reinstall Ubuntu using Wubi, but I can handle that.

I just need help getting rid of Ubuntu and merging the partitions back together. I'll need fairly detailed steps, while I'm not new to computers, I'm not a whiz either. 

Thanks in advance!

HI and welcome, you can use the live cd to delete the Ubuntu partition and resize you windows partition. This link has good info on fixing the mbr for windows before you delete your partition
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

### Post by whitewolf1218 on 2008-05-04
None of the Super Grub Disk downloads are working for me, and I don't understand how to use the LiveCD to delete the Linux partition and merge it back with my Windows partition. 

I don't have the XP discs for this system, so fixing the bootloader that way is out of the question. 

Ugh... why is this so complicated?

---

### Post by FastZ on 2008-05-04
Look for the GParted LiveCD and burn that to a CD and then boot from it to delete the ubuntu partition and expand the NTFS partition to fill the empty space.  Don't forget to fix your MBR or else you wont be able to boot back into Windows after you delete the Ubuntu partition.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

To fix your MBR do the following:


[LIST]
[*]Insert your Windows XP CD and restart your computer.  Be sure the CD drive is the first boot device.
[*]When prompted, press any key to boot from CD.
[*]Select "Repair Windows" (DO NOT select re-install Windows or Install Windows).
[*]Enter the Recovery Console.
[*]Type in the Admin password.
[*]When the Recovery Console is loaded, you'll be at a command prompt (c:\windows).  If needed, change directory to c:\ (**CD c:\**) to the root directory.
[*]Type **FIXMBR**
[*]Follow all the prompts -- (yes, this is what you want).
[*]Restart.  Your Windows is now fixed.
[/LIST]

---

### Post by whitewolf1218 on 2008-05-04
> **FastZ said:**
> Look for the GParted LiveCD and burn that to a CD and then boot from it to delete the ubuntu partition and expand the NTFS partition to fill the empty space.  Don't forget to fix your MBR or else you wont be able to boot back into Windows after you delete the Ubuntu partition.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

To fix your MBR do the following:


[LIST]
[*]Insert your Windows XP CD and restart your computer.  Be sure the CD drive is the first boot device.
[*]When prompted, press any key to boot from CD.
[*]Select "Repair Windows" (DO NOT select re-install Windows or Install Windows).
[*]Enter the Recovery Console.
[*]Type in the Admin password.
[*]When the Recovery Console is loaded, you'll be at a command prompt (c:\windows).  If needed, change directory to c:\ (**CD c:\**) to the root directory.
[*]Type **FIXMBR**
[*]Follow all the prompts -- (yes, this is what you want).
[*]Restart.  Your Windows is now fixed.
[/LIST]

Thanks FastZ, I'm downloading GParted now. 

I do not have an XP cd, but I used these instructions and it worked perfectly:
[http://users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe](http://users.bigpond.net.au/hermanzone/p18.htm#MbrFix.exe)

---

