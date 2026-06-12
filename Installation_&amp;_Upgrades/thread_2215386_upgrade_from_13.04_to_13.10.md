---
title: "upgrade from 13.04 to 13.10"
date: 2014-04-06
forum: Installation &amp; Upgrades
---

### Post by Aero_Nexcom on 2014-04-06
I recently upgraded one of my machines from 13.04 to 13.10 using the upgrade window. All went smoothly on the upgrade. The Upgrade finished and I restarted the system. The system hung at the System V line in the reboot process. Watching the screen, It would periodically refresh but get no further in the process of booting. Further, it would occasionally allow me to log in at the command line. I logged in and ran startx (as I have found a suggestion elsewhere on the web to try) and looked at that log. It indicated that it had a problem with my Nvidia-173 driver. Nvidia-173 is an old driver. So on a shot, I removed the NVIDIA-173 driver from my system. This apparently reset my X files so the system could come up in basic video mode (almost immediately). I then updated my video driver to a later version which Ubuntu is happy with.

So caution to upgraders, if you have a very old video driver, the upgrade may not deal with it and result in your having to fix it by hand.:lolflag:

Also thanks to those out there making suggestions on how to fix problems. You have helped me multiple times.:p

---

### Post by sudodus on 2014-04-06
Welcome to [posting in] the Ubuntu Forums :-)

and thanks to sharing your solution :KS

---

### Post by grahammechanical on 2014-04-06
I have had the opinion for a long time that the first thing to do before upgrading is to de-activate the proprietary video driver. The second thing to do is to revert the desktop as far as possible to a default desktop.

Regards.

---

