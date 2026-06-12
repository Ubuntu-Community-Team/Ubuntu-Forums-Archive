---
title: "Nvidia API Mismatch"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by ScotchontheRocks on 2007-04-22
This is not a complaint, just an issue I ran into today and how I resolved it. Hopefully someone else will find it useful.
I just upgraded this morning and had an issue with X system not loading after reboot. It gave me a nasty-looking screen that said something to the effect of "API Mismatch. Kernel is 1.0-9755 but X module has 1.0-9631"
The first thing I did was to try and re-install via aptitude, which was not successful.
Then, I went into recovery mode and went to /etc/X11 directory. There were two files in there:  "xorg.conf" and xorg.conf.backup". I did a sudo nano of the two and found an interesting difference. The backup file listed:
Identifier  "NVidia ...blah blah"
Driver  "nv"
BusID  "PCI:1:0:0"
The OTHER xorg.conf file did not have this information. So, I made a new dir called "backup" copied the xorg.conf to it. Then, did a sudo nano again of the xorg.conf file and changed it to match the display settings of the .backup version and rebooted. Now I have a GUI.
I'm not sure if I did everything "right", I'm still pretty new at Linux. But, I wanted to share this with the community in case someone else had the same issue and could try this before panicking or reformatting.

---

### Post by GeDaMo on 2007-04-22
If the driver in your xorg.conf is now nv, you're not using the binary nvidia driver and you won't get 3D acceleration.

---

### Post by neumeka on 2007-04-25
I have had this exact problem.  I had a GForce 6000 running on Edgy just fine.  I used envy to install it.  When I upgrade to Feisty, I got a blue screen when X tried to start up.  The error that it gave is "API mismatch.  Nvidia kernel has version 1.9775.  X module has 1.9631".  I then purged linux-restricted-modules-2.6.20-15-386, nvidia-glx, and nvidia-kernel-common.  Then I tried to install nvidia-glx.  When that didn't work, I removed the packages as before and installed nvidia-glx-new and the same thing happenend.  Any suggestions?

---

### Post by neumeka on 2007-04-25
Ok I fixed the problem.  What was happening is that nvidia-glx was the wrong package for me.  I needed nvidia-glx-new.  However, when I installed nvnidia-glx-new I went to the restricted driver manager and check the enable button.   That was my problem.  For some reason, it uninstalled nvidia-glx-new and reinstalled nvidia-glx.  So instead to fix the problem, I purged, then installed nvidia-glx-new.  Then I ran "sudo nvidia-xconfig" and rebooted.  Now everything works fine.  It looks like the restricted driver manager was messing me up.

---

