---
title: "Garbled picture with nVidia driver after upgrade"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by jeff303 on 2006-06-28
Apologies for starting a new thread on this already-beat-to-death topic but I had issues that didn't quite match up with others' I saw.  I had a fairly smooth upgrade from Breezy-Dapper using the GUI tool.  However, after rebooting again for the first time, the machine froze, I think, right when xserver attempted to start (non-blinking cursor appeared at top-left of screen, no response to input).  In this case I had to hard power-down and power-up.

After reading about some of the issues here, I tried some of **tseliot**'s stuff outlined here: [http://www.ubuntuforums.org/showthread.php?t=187177]("http://www.ubuntuforums.org/showthread.php?t=187177") and his script here [http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html").  Note I also followed his "special" instructions for my card (Geforce 440 Go).  

In both cases, I got the same result after running the script, or the nvidia-xconfig command.  After rebooting, now it no longer locked up when x started (woo-hoo), but instead the screen was garbled.  It was mostly black with a few horizontal gray lines in the upper portion.  There were also (seemingly) random green and red vertical lines across the screen.  The other notable feature was that there was a bright portion (mostly white) near the middle of the screen that seemed to fade after a few seconds.  Input apparently was working, however, since I was able to login and issue an X-reset command via keyboard.  Also, when rebooting into recovery mode and running dpkg-reconfigure xserver-xorg and selecting "nv" driver, then X started well on the next reboot.

For now I'm happy sticking with this solution (nv driver), but eventually I want to work with OpenGL apps, which means getting the nvidia-glx drivers working again (not to mention nvidia-glx-dev which is a whole different animal).  Any ideas on things to try?  If a screenshot of the garbled mess would help I can try to capture one, but I'm not sure how.  I'm not afraid to experiment with things since I have all my important data (in ~) on a separate partition which I can recover from a LiveCD if necessary, and reconfiguring xserver to use nv seems to make things happy again when I screw them up.

Again, any suggestions/help are much appreciated.  Thanks for your time.

---

