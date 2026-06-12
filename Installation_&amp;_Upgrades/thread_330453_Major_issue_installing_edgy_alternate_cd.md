---
title: "Major issue installing edgy alternate cd"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by patsissons on 2007-01-03
I decided to do a fresh clean minimal install of edgy on my server at home today.  The installation went very smoothly, but once the install was finished and I was prompted to remove the CD and restart (which I of course did), the system was stuck in an endless loop of posting then restarting.  More accurately, the system would post, grub would load, then upon attempting to load the kernel the system would restart.  After a LOT of tedious trial and error with boot flags (all of which didn't work), I was about to give up and call it a botched install (and continue with a reinstall).  As I booted up to reinstall I noticed that there was a rescue mode on the CD, so I decided to check and see if anything was wrong in /boot (maybe a typo in menu.lst).  No errors were present, but I figured maybe the kernel was just bad.  So  I installed the linux-generic metapackage and then rebooted and chose the new kernel.  Everything worked fine.

I can only conclude that the linux-server package (which the alternate CD installs by default and without choice) is not designed for older processors.  Either that or there is a problem with the server kernel (which I highly doubt).  If anyone else experiences these problems, the solution is to simply boot into rescue mode after installing, then start a console in your recently installed root partition, then apt-get update && apt-get install linux-generic.  Restart once more and this time choose the proper.  You can also remove the linux-server and dependent package, however, to the best of my knowledge this has to be done manually for each package (i.e. each dependent package must be removed)

Just fyi, my system IS quite old.  It is composed of many spare "throw away" parts.  I believe the CPU is 375MHz Duron, 256M ram, a very old video card, and other old generic parts.  The CPU is definitely i386.

---

### Post by Sef on 2007-01-03
I would look at using [xubuntu]("http://xubuntu.org/").  It is made for older machines.  It is XFCE + Ubuntu.

---

### Post by patsissons on 2007-01-03
I was using xubuntu before, but it is still quite sluggish at times.  Currently i use a WM called dwm on my laptop which has equally low system specs as my server (hey, I can't complain, it cost me $20 CAN).  dwm runs smooth on just about anything over 33MHz.   I am going to tweak my config and patch the source for dwm with some modifications I have made to it and then I will post the results for any edgy users that wish to give it a try.

---

