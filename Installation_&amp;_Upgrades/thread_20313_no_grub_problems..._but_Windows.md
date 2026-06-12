---
title: "no grub problems... but Windows?"
date: 2005-03-16
forum: Installation &amp; Upgrades
---

### Post by acada on 2005-03-16
Hi!
As described here:
[http://www.ubuntuforums.org/showthread.php?t=20110](http://www.ubuntuforums.org/showthread.php?t=20110)
I had Windows Xp on master hard drive hda and installed Ubuntu on slave hard drive hdb. Grub wouldn't want to boot in any system and I got Error 21 at Stage1.5. 
The idea that I got from Azz was correct! Grub was confused by the BIOS. In fact, hdb was OFF in the Bios! After changing that into AUTO, Grub booted in i Ubuntu with no problems!
Thank Azz for this!! :p 

My problem now is: Windows cannot be found anywhere! 
I installed Grub twice. The first time, Grub told me that  Win Xp was found on the computer. When I installed Grub a second time (since Grub wasn't able to let me in any OS I thought that it was badly installed) Windows was gone and not recognised. So Grub doesn't see Win Xp!
I then decided to create a boot floppy for Ubuntu and restore the MBR as described in 
[http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)
using the Recovery Console and the fixmbr command. No effects! Not even the Recovery Consol could see a Win version on my hda.
I then installed Win Xp on a third HD, used it as master and coupled my first hda as slave. The system recognised the hda but told me that it was not formatted! ](*,) 

Do you think there is a way to recover my data from hda, if not restore the Win Xp version I had on it?
thanks!
cada

---

### Post by orca on 2005-03-16
Which system did you use to look at the original had, Windows XP or Ubuntu? 

If you need to recover data from a corrupt drive, there are quite a few tools you can use. I used NTFS dos to recover data I lost few years ago. Some of my friends tell me that there are few freeware tools out there which are quite good as well. 

Another option, if you are not using Ubuntu is to load up the live CD and see if you can see the partition in had. 

Hope this helps.

---

### Post by acada on 2005-03-16
thanks! 
I would like to try first to restore Win Xp if possible! If it doesn't work I will surrender and try to recover only the data as you suggested.
There should be a way to repair only the boot sectors of my hda. I hope.  [-o<  This evening I will test the FIXBOOT and BOOTCFG commands in the Recovery Console in Xp.

cada

---

