---
title: "Dual SLI Video Card problem"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by StKunze on 2007-11-08
Note this is with a single monitor, not dual monitors, but the system uses dual SLI video cards for performance.

Video Card 	Dual NVIDIA GeForce Go 7950 GTX
Chipset 	NVIDIA nForce4 SLI (CK804)

I'm a relative newbie (first confession) and installed Ubuntu 6.10 from a downloaded disk image off the official site, but appeared to have done the wrong thing as I ended up with no GUI. So I trawled the support forums and found instructions for installing x, did that apparently successfully, but when I boot into (command line) ubuntu and do startx, the screen simply goes blank, and I have to reboot to get back to the command line.

I guess it may be something to do with the xconf files(?), but I'm not sure, and don't want to try advice given for dual monitors because it is only a single monitor.

As the system is dual boot, WinXP still works fine. 
Ubuntu run from a LiveCD tries to give me a GUI but fails (blank screen again)
DSL run from a LiveCD works and gives me a GUI, so I can get some kind of Linux GUI up and running if neccesary for fault diagnosis (but I want to run Ubuntu).

I've been running Ubuntu 7.10 on a laptop and that's fine (single nvidia card though).

Thanks in advance for any help!

---

### Post by Craigus on 2007-11-08
Probably related to this issue:

[http://ubuntuforums.org/showthread.php?t=588671]("http://ubuntuforums.org/showthread.php?t=588671")

If you use non-randr-aware nvidia drivers, it should be OK.

---

### Post by Huntedmason on 2007-11-16
I'm running dual evga GeForce 7600gs under sli config on my system and ran into a similar problem installing ubuntu 7.10.  After knocking my head trying to get it to work I noticed my system was still running but after passing the initial install stage from CD to harddrive my screen would go blank.  I decided to unhook my monitor from the primary video card and plugged it into the secondary card an viola all of a sudden I had the picture back and was able to finish the install.  I had to reduce the top and bottom panels to be able to finish the install, but once I updated the video drivers to the unsupported nvidia driver everything works perfect.  However the one drawback is that to run ubuntu I still have to switch from the primary to the secondary video card by manually moving the display cable.  Not fun, but it works.  Hope this helps!:)

---

