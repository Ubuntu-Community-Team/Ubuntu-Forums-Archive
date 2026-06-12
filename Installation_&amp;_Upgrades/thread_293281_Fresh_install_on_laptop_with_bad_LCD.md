---
title: "Fresh install on laptop with bad LCD"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by martincj on 2006-11-05
The goal is to install Ubuntu on a laptop, but there is a catch. The laptop has a defecting primary monitor.

With a CRT monitor plugged into the back, and the live CD in the drive, everything boots up just dandy until it tries to load the desktop. At this point, though the startup music can be heard playing, the screen goes all haywire.

I'm assuming that at this point x-server is using the (broken) laptop monitor as the primary display and isn't sending a useful signal to the analog (CRT) display.

Can something be modified on the install CD to force Ubuntu to use the CRT instead of the LCD?

Any help would be greatly appreciated.

---

### Post by amohanty on 2006-11-05
Other than snipping off the connector cables to the LCD :) I dont know?

Can you see anything at all?
What if you try to boot into the recovery terminal and reconfigure X?

AM

---

### Post by martincj on 2006-11-05
Thanks for the tip. Suppose I successfully can boot up into the recovery mode, what exactly do I need to configure in X? (Note: don't worry about insulting my intelligence, feel free to respond as though I don't have a clue what I'm doing - it's mostly accurate.)

---

### Post by amohanty on 2006-11-05
**sudo dpkg-reconfigure xserver-xorg**

AM

---

### Post by martincj on 2006-11-06
Thanks again for the advice. However, I think I may have been unclear on exactly what the situation is.

The laptop has NOT had ubuntu installed on it ever before (i.e. booting into recovery mode doesn't seem to work because there is nothing to recover). The goal was to convert a former XP installation into an ubuntu installation.

With this being the case, is there a way to extract the .iso file for the ubuntu live CD (using iso buster or something similar) and alter the xorg.conf file such that the default display is switched from the digital (and in this case, broken) monitor to the analog monitor jack? Could the iso be recompiled, burned to a new disc, and then installed?

Thanks in advance for any help you can give.

---

### Post by amohanty on 2006-11-06
So did reconfiguring xserver work?

The thing is the xorg.conf file is created during the install, if you recall, it does prompt you about the resolution of stuff and all that. So I am not sure if you could modify any file to make that happen.

ALso check if there is an option in the BIOS to set the display to CRT instead of LCD (mine does, and its a six yr old laptop). 

HTH
AM

---

