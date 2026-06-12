---
title: "read-only file system after fresh install"
date: 2014-11-08
forum: Installation &amp; Upgrades
---

### Post by alexw2 on 2014-11-08
I know this is a "known issue" in previous versions of Ubuntu (see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1063354](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1063354)), but I haven't seen anything specifically related to Ubuntu 14.10.  Also, I haven't seen any specific fixes for the issue even in previous versions.  So, I'm posting!

Basically, I recovered two old Dell Pentium 4 desktops from a dumpster a few weeks back.  Between them, I managed to cobble together 1GB of memory (which passes the BIOS built-in memory tests), an E210882 Dell mobo+processor, an addon video card (oooh), and an Hitachi 80GB IDE hard drive.  When I booted off the drive, it was running an install of Windows XP, heavily infested with Free Poker spyware and some photos of the previous owner making duck faces.  Needless to say, I wiped the drive and installed Lubuntu to prepare it for its new life as my personal NAS box.

I'm new to Ubuntu, so I did the Linux Live USB route, loaded up an iso of Lubuntu 14.10 i386, and everything seemed to be OK after booting up.  So, I went ahead and ran the script to "Install Ubuntu".  It completed installation without a hitch, after which the updater started doing its thang.  Here's where I started running into trouble.  I left it alone to install updates, and when I came back, I was presented with the login screen.  I entered my credentials, but instead of a beautiful new desktop, my machine promptly rebooted itself.  This time, it took me to a blue screen with "Lubuntu 14.10" slightly off-center, and a status indicator that just kind of hanged.  

Since then, I've tried rebooting, with various degrees of success.  Sometimes I do manage to boot Lubuntu successfully, and I can use it for a while until I am suddenly hit with the "read only file system" error.  The 7+ year old HDD seemed to be the reasonable culprit here, so I ran the built-in disk manager and ran both the short and extended SMART tests.  Behold - SMART tells me that everything is OK!  Drive temp normal, attributes all above threshold, yadda yadda.  I've run dmesg, which spits out a bunch of "error in low memory" messages.

So, do I have a hardware failure on my hands?  Or, is the drive technically "fine", but does Ubuntu hate me for using IDE/PATA?  Do I need to put on some Evanescence and make it a MySpace page to remind it of the good ol' days?  Should I try fsck'ing around with the file system?

---

### Post by mörgæs on 2014-11-09
Hi, welcome to the fora.

> **alexw2 said:**
> I've run dmesg, which spits out a bunch of "error in low memory" messages.


This is related to RAM, not the hard disk. If you have more than one RAM module, have you tried taking them out one by one to see the difference? 

Beware of static electricity when touching the RAM modules.

---

### Post by alexw2 on 2014-11-09
Ok that's what I thought, but I ran the BIOS memory test and it didn't find any problems.  The RAM modules are as old as the rest of the components, but I didn't think RAM went bad all that often.  Unfortunately they're each only 512MB, so I'm not sure if even Lubuntu will tolerate that.  I'll try them individually, but I might just have to buy some replacement memory if I can even find it for sale.

---

