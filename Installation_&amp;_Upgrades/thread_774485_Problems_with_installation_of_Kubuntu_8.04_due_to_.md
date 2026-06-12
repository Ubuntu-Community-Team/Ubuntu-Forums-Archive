---
title: "Problems with installation of Kubuntu 8.04 due to Radeon driver  (a little angry)"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by hardhu on 2008-04-29
I have tried to install kubuntu 8.04 kde 4 remix on an Acer Aspre 5024 notebook, which has an Ati Mobility Radeon X700. I could boot the live cd, I have chosen to install, but when I got to the screen where the installation process begins, I had huge fonts (I could see only the word 'Welcome' on the half upper side of the screen), and I couldn't go on. The same happened if I only run the livecd: when I got to kde desktop the font problem was the same. And the same happened when I made an installation from the alternate cd.

After investigating a while, I discovered that this problem has certainly something to do with radeon driver. In fact, I have just been able to get the correct fonts by changing the driver with the proprietay one fglrx.
This has been not simple, the steps I have made are the following:
- first I started with the installation I have done with the alternate cd;
- then I got to a console (ctrl+alt+F1)
- then I have used aptitude to download and install fglrx video driver (remember that i couldn't do using kde hardware driver manager since I couldn't use the desktop!)
- I tried to use the command 'aticonfig --initial' to create a new /etc/X11/xorg.conf, but it failed since there was no Driver line in the video device section;
- I added the line 'Driver "fglrx" and I restarted x server;
- the screen flashed a while, and then it became black; I have been forced to make a reboot with ctrl+alt+canc since I couldn't get to the console anymore
- in the reboot process, I selected the single user mode so that the x server didn't start;
- I checked the /var/log/Xorg.log and I saw that the problem was related to depth set to 8, that was not supported by the fglrx driver, so I edited the /etc/X11/xorg.conf and I have added a line with "Defaultdepth 24" in Section "Screen", and I finally could get the desktop working.

I am an experienced linux user, and so I could solve this problem, but what would have a new user done?
If you really want to fix bug number 1 in launchpad, these installation problems should really not be present :(:(

---

