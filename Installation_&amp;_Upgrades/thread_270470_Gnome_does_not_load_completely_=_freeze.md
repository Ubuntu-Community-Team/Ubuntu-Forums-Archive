---
title: "Gnome does not load completely = freeze"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by Death4Hire on 2006-10-03
Hi!

I just installed Ubuntu successfully on my machine (Compaq Presario R3000 - Intel P4 2.4Ghz, Ati Radeon 9000). My first install, was successful but on my first use, when Ubuntu is about to start Gnome, it does it usual loading stuff and logon sound starts, but somewhere during the loading of Gnome it stops abruptly (noticeable with the sound being cut too) and I'm shown with a desktop and an incompletely loaded desktop panels (sometimes some objects are missing like clock, power button, desktop switcher, etc -- randomly). I can click stuff on the desktop but the panels are not clickable/interacting.

Then, I reinstalled Ubuntu again. Install successful. At first try it was ok! No problems but on next reboot and the following after, same problem.

I need help on how to fix this or determine what is the problem. :D

---

### Post by Death4Hire on 2006-10-04
I just found out that the problem is probably because of my ATI chipset driver. Whenever Ubuntu uses the "ati" driver this happens. I changed it back to VESA and lowered my resolution from 1280x800 to 1024x768. I tried to install my ati driver (fglrx) throught the instructions in the Ubuntu wiki but still no go. Mine is Ati Mobility Radeon 9000 (belongs in the chipset line that ATi no longer cares about). Anyone here who has successfully installed ATi driver for Radeon 9000 with 3D graphics acceleration enabled?

---

