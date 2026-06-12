---
title: "[SOLVED] Hard problems with Gutsy on Asus F7kr"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by squalho on 2008-01-13
Hello everybody,
I am finding a lot of troubles trying to install ubuntu 7.10 on my brand new Asus F7KR.
I downloaded the installation cd, both 64 bits and 32 bits and burned them. Put in the laptop and booted. The live CD boots, it shows me the very first selection (Start or install ubuntu, start ubuntu in safe graphics mode, etc) then is begins to load the system.
After a few seconds it gets to "Starting the GNOME display manager" and there it stucks. The 64 bit cd just stays there, the 32 bit cd starts doing something weird (they're burned correctly, sure).
My screen starts flashing, trying to start the graphic mode, but it can't. After a few trials it shows me a windows (in text mode) telling me that there was a problem loading the graphic server: it has been shut down about 6 times in the last 90 seconds (wow!).
I really don't know what to do because I can't start the live CD, get to a shell or whatever, i'm stuck looking at my screen flashing...
Maybe the alternate cd install can do something?
Oh, by the way, my laptop's graphic card is an ATI HD2400.

Vittorio

---

### Post by cmakula1 on 2008-01-14
Try doing your install under "Safe Graphics" mode.  When running the live CD, it'll only give you 800x600 for graphics, but I think your video card is listed as having "Restricted Drivers" (kind of like the modem and wireless on my Dell), so it won't prompt you to add the drivers until after Ubuntu is installed.

Good luck!

---

### Post by squalho on 2008-01-24
> **cmakula1 said:**
> Try doing your install under "Safe Graphics" mode.  When running the live CD, it'll only give you 800x600 for graphics, but I think your video card is listed as having "Restricted Drivers" (kind of like the modem and wireless on my Dell), so it won't prompt you to add the drivers until after Ubuntu is installed.

Good luck!
The live cd doesn't work at all. I managed to install ubuntu using the alternate. Then I've been able to install the video driver thanks to the Envy utility. At this time I can see the desktop, but no 3d effects are available, and my wireless card doesn't work (Atheros AR5007EG).
I think that my laptop has got serious hardware compatibility issues, so I thinkg I'm going to wait to see whether with time they will be solved....

---

### Post by Partyboi2 on 2008-01-24
have you looked at trying to get your wireless up and going?
[http://ubuntuforums.org/showthread.php?t=554531](http://ubuntuforums.org/showthread.php?t=554531)

---

