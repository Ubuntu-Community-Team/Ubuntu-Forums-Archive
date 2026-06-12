---
title: "Help, error 16 and can't access my PC"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by Danny Builth-Snoad on 2005-11-25
I might have done bad, I installed 5.10 onto my main work laptop as a gentle toe in the water of linuxdom yesterday and now it won't boot. I'm getting a error 16 and doing a bit research it looks like this isn't uncommon.

the machine is a thinkpad T41 w/- 40Gb drive, during the installation I took the option of creating a new partition from the largest available space (only 3Gb) and opted to install grub. Since then it won't reboot from the HDD and gives erro r 16. I reran the install, rectreated the partition etc but the same again

I'm not overly technical and a complete newbie at linux so I'm really after a fix so I can access XP on my machine as I've got a bunch of work to do. If that involved removing Ubuntu and/or grub and trying again next week on a different PC that's fine by me. 

Does anyone have a fix for this problem? All help greatly appreciated

cheers
danny

---

### Post by dmxubuntu on 2005-11-25
I haven't looked up what "error 16" would stand for, but here is a quick way to get back to XP, from memory, having had to do so many times myself.

Use your XP Install CDs and boot from it. Drop to the console. From the console, you can issue a "fixmbr" command (see [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx))

This will reinstall XP's boot sector and the Windows bootloader will then be called instead of Ubuntu's.

Hope this helps a little. :???: 
Denis

---

### Post by Danny Builth-Snoad on 2005-11-25
Thanks for the quick reply Denis, yes that helps a lot. I don't have the XP install disk (it's a work SOE) but I'll borrow one from my neighbour and have a shot

thanks again
d

---

