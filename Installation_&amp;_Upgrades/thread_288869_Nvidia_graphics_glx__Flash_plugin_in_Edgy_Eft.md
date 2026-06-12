---
title: "Nvidia graphics glx / Flash plugin in Edgy Eft"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Extr3me on 2006-10-30
OK, just recently upgraded to Edgy Eft and noticed that when you install the Flash plugin Firefox bombs when you try to load a flash enabled page.  It starts to load the page, and then when it gets to the flash component just exits Firefox. Total pain, as I had just got Firefox, flash and sound running sweet on my dapper install.

Never mind, I thought, I will install the glx driver so I can at least skive at work playing Enemy Territory.  Disaster, the x-server bombed on bootup complaining about some dodgy driver.

Aha, I thought, I will hit the forums and see what comes up. Not a lot, although someone had previously recommended that 24-bit colour depth might sort out some problems when getting flash to work.

So I checked my install of the flash plugin and the nvidia glx driver and set about hacking my xorg.conf to work.  Make sure you make a backup if you ever do this as it can all go wrong and you are left with a terminal on bootup trying to remember which one of the umpteen changes you made probably screwed it up!!

Right this is where it gets a bit confusing, as I got both the glx driver and flash going in one go, so I wont be fiddling with it.

To get flash to work correctly, you have to be in 24-bit colour depth and the same is to be said for the glx driver.  What I did was set the bit depth to 24 in the /etc/x11/xorg.conf first, and then noticed that the screen had gone all fuzzy. But, and most importantly, flash wasn't bombing firefox any more.

So I thought, well I might as well try the glx driver as well as it won't really get much worse (the screen looked terrible).  Editting the /etc/x11/xorg.conf file again so the graphics driver was 'nvidia' over the default x.org 'nv', hitting <Ctrl>-<Alt> & <Backspace> and blam.  We have working flash and glx.

This was certainly the case for me on my nvidia go equipped laptop, so if it helps anyone that would be cool.  Good luck, and don't forget GLX makes the screensavers look really cool and isn't just for games. (You can tell your work admin that if he is curious why you *need* it!!)

Extr3me

---

