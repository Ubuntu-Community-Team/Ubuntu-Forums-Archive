---
title: "I HATE Grub - can anyone help me love it?"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by ed4becky on 2011-05-11
OK, here's the REAL problem...

I have a desktop with a 60GB primary drive, and 4 RAID5 drives.  /dev/sda is the 60G drive, and according to the bios is the primary drive.  I have Ubuntu server running on it.  The file system is reiserfs.

EVERY time I do a major upgrade that involves GRUB2, the system will no longer boot, and I have to use the Live CD, reinstall GRUB to /dev/sda.  It usually takes me an hour or more booting and rebooting to sort all this out. 

**This time with Natty I have spent a couple hours and STILL can't get it working.**

I can boot fine into /dev/sda using the Live CD,, and from there I have:

Tried reinstalling Grub2 to /dev/sda 
Using the Chroot method to reinstall
Uninstalling and installing GRUB legacy
Uninstalling grub legacy and reinstalling GRUB2.

I was getting:
error: symbol not found: 'grub_env_export'

Then display "grub rescue>"

I sometimes got a file not found error

I am currently getting an error: sparse files not allowed.

Should I consider a different boot loader?  This is a single boot system (whatever the latest image for Ubuntu is).  What boot loader is best?  For my configuration its obviously not GRUB for some reason.

Help?

---

### Post by wilee-nilee on 2011-05-11
How about a free bump.:popcorn:

grub is well....an acquired taste, I would help if I had even a clue with raid.

---

### Post by Quackers on 2011-05-11
I had the 'grub_env_export' error but wasn't using raid.
I solved it by purging then re-installing grub with drs305's guide below.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by ed4becky on 2011-05-12
Quackers, I tried those suggestions (thats how I spent my evening <grin>, but no help.

Anyone have suggestions for alternatives to GRUB?

---

### Post by ottosykora on 2011-05-12
>Should I consider a different boot loader? <

yes

I am also about enough fed up with that so much, so I went back again to some commercial product. I am using old bootmagic (from powerquest) but this may get some problems with some current partition formats. The latest of my systems uses product from acronis and this works fine, installed with a mouse click, configured with a mouse click and uninstalled with a mouse click reliable.


I can not understand why there is so much effort to develop strange and not very useful GUI called unity, but important things like bootmanager or installer system are left out. I think the energy put into the unity could produce bootmanager deserving its name and not get stuck with this never finished construct of grub.

---

