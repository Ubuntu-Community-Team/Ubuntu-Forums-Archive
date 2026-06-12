---
title: "[SOLVED] How to upgrade dual boot system without messing up?"
date: 2008-02-21
forum: Installation &amp; Upgrades
---

### Post by merobson25 on 2008-02-21
Sorry to start a new thread, but all I can find is information about how to FIX a broken dual-boot system, and I'm trying to prevent breaking mine in the first place.

I have been running Feisty for awhile now, but I'm pretty newbie and have little experience fixing Ubuntu problems. When I set up Feisty on my laptop, I partitioned the hard drive so that XP is on one partition, with separate partitions for / and  /home (and, of course, swap). The last partition is a  FAT32 shared partition. I installed GRUB onto the Ubuntu / partition, so the machine boots using the Windows bootloader, with Ubuntu being an option that can be chosen at start-up. The guide that I used to do all this is 
[COLOR="Blue"]
[http://physicsmajor.wordpress.com/2007/03/03/my-ubuntu-installation-on-thinkpad-r60-dual-boot-with-winxp/]("http://physicsmajor.wordpress.com/2007/03/03/my-ubuntu-installation-on-thinkpad-r60-dual-boot-with-winxp/")
[/COLOR]
My question, after that long-winded wind-up, is how to install Gutsy 1) without wiping out everything on my /home, and 2)  keeping the system so that it boots using the XP bootloader. I presume that I need to use the install disk rather than the upgrade path, but I am concerned (perhaps unnecessarily) that this will either wipe out /home or make it unusable.

Thanks for any guidance.

---

### Post by forestpixie on 2008-02-21
not at all sure about the bootloader - but you might just have to redo that, follow the same route to install grub as you did before

on to the /home partition 

as long as you have a seperate partition then it will be fine as long as you make sure that you go for manual partitioning, which you must have done for feisty then - 

you need to set mount point for the / partition again as / and let the install format it 
for the /home - set mount point as /home but DO NOT format it 

it should find you're swap

---

### Post by merobson25 on 2008-02-21
Thank you for the quick answer. Just one clarification- how do I prevent the install from formatting the /home? Is there an option (checkbox, drop-down) that asks whether or not to format each partition?

---

### Post by forestpixie on 2008-02-21
yea - there's a box to tick to make it format - but obviously check it isn't ;)

might also be good to make sure you have backups - anything can happen in the next few hours :D

Of course that is how it is with the livecd - absolutely no idea about the alternate install - but the info is about

---

