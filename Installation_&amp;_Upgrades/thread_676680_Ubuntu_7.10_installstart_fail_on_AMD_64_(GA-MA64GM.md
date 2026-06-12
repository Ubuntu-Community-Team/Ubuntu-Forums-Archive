---
title: "Ubuntu 7.10 install/start fail on AMD 64 (GA-MA64GM-S2H)"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by DuncanG on 2008-01-24
Aiming for MythTV install, mythbuntu install failed, so did 7.10 Ubuntu graphical install. Have disabled floppy and HPET. Text install of 7.10 seemed OK, but on reboot got blank screen. Several reboots, one time had small circle (like 'loading' on firefox, but not animated).
I can start in restricted mode and have command-line access as root. What command should I try to get Ubuntu started, and see what the problem is ?
Motherboard: GA-MA69GM-S2H, CPU: AMD 64 BE-2350, 1GB RAM, 1TB Samsung SATA drive.
TIA, Duncan

[edit] startx gets me into the GUI, though as root. If I su - duncan I get "X: user not authorized to run the X server, aborting."
Got past this, I get a window with "failed to initialize HAL!". Thanks for 2000 joke :-(

---

### Post by djdarrin91 on 2008-01-24
try startx. i'm a noobie but that worked for me,good luck.

---

### Post by DuncanG on 2008-01-24
The further I get in the recovery mode, the more problems I see. I don't have network access, which may be a function of recovery mode I guess.
Is there a change to the normal startup commands I could make to get some debug:
root (hd0,0)
kernel /boot/...
initrd /boot/...
quiet

To start, I removed "quiet splash" from kernel line, and final "quiet" line". Boot, which hangs, but press CTRL-ALT-F1/2 (or thereabouts) and get command line. startx then starts and have net access. Download latest updates, and also ATI drivers. Alter /etc/usplash.conf to set resolution to 1024x768. All OK.

---

