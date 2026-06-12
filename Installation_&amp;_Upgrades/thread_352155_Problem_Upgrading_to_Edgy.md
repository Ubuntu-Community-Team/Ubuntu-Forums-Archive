---
title: "Problem Upgrading to Edgy"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by Dagonus on 2007-02-02
So, I tried upgrading to Edgy from Dapper using the terminal command. 

Normally, I'm a paranoidand backup things at the slightest changes, but I had this crazy idea to live dangerously and not grab copies of some important document. Mistake numero uno. 

The upgrade downloaded fine. It started installing fine.

Then it gave me an error on update-manager for /var/log/dist-upgrade/

Now the X-server won't load. I tried using an old version of xorg.conf that I had backed up and that didn't get the x-server to load. So then I figured "Alright I only need to grab a few files off and then I can just smoke the system and do a fresh install." Nice thought, but the term didn't want to give me access to my flashdrive. Maybe I mounted it wrong, but it was giving me Access errors. Same thing with an hdd in an enclosure kit that I tried plugging in. 

"Ok, plan C: i'll load up the Dapper live and just mount the internal hdd and then copy the stuff to my flash drive that way so that I can then easily save the data and then burn the system" Wrong again. The Live for some reason doesn't want to mount the internal hdd, though it gives me no reason why. 

So what I need is either a way to complete the upgrade to Edgy or to eb able to get the flash and the internal hdd working at the same time, which will probably mean reteaching or at least walking me through a mount since I probably wasn't mounting right. 

Thanks in advance.

---

### Post by Dagonus on 2007-02-03
Well I was able to use :

[http://www.ubuntuforums.org/showthread.php?t=187177](http://www.ubuntuforums.org/showthread.php?t=187177)

to get the XServer semi functional again. A whole lot of error messages during the Deconfig and at boot, but it got running. That's enough for me to bail out what I need and then just format the whole thing for a fresh install of Edgy.

---

