---
title: "Available drivers?"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by ubuntu1sttimer on 2005-05-05
Am trying to install ubuntu on an older machine.  5.04 seems to have a problem with my Intel I470 video chip.  640x480 just does not do it especially when some modules don't support that low a resolution.  Am willing to purchase a new card but don't want to keep buying till I find one that works.  How/where do I find a list of available drivers for ubuntu 5.04.  Not just video but all device drivers as I may be changing other things before I get done with this challenge.

---

### Post by bored2k on 2005-05-05
[QUOTE=ubuntu1sttimer]Am trying to install ubuntu on an older machine.  5.04 seems to have a problem with my Intel I470 video chip.  640x480 just does not do it especially when some modules don't support that low a resolution.  Am willing to purchase a new card but don't want to keep buying till I find one that works.  How/where do I find a list of available drivers for ubuntu 5.04.  Not just video but all device drivers as I may be changing other things before I get done with this challenge.[/QUOTE]
 Before you go buying stuff, try reconfiguring xorg
 sudo dpkg-reconfigure xserver-xorg && sudo reboot

---

### Post by nad on 2005-05-05
The list is a little dated, but it is an excellent resource:

[http://www.tldp.org/HOWTO/Hardware-HOWTO/](http://www.tldp.org/HOWTO/Hardware-HOWTO/)

You can also peruse the /lib/modules/(uname -r) directory for drivers compiled with your kernel, as well as the /boot/config file for your kernel, /usr/X11R6/lib/modules/drivers for graphics drivers and of course xfree86.org .

---

### Post by ubuntu1sttimer on 2005-05-06
Checked for the available  video drivers as directed and found that it did not mention Intel I740 but has Matrox G450.  Just happened to have a spare board of that type .  Installed it and is working fine.  Now I can get to the buttons at the bottom of screens that were unavailable at 640x480.  There are a couple other problems.  When the system is fully up and running, I can start learning how to control the fine points like importing a video driver for the I740.  -  Thanks

---

### Post by nad on 2005-05-06
Your welcome. Glad I was able to help.

---

### Post by MarkyMac on 2005-08-21
I have reinstalled Ubuntu 4 times now.
I am running a Pentium III 866 MHz running at 433E, mobo needs to be updated.
The video card reads as an Intel i740 and I think it is an 8 MB 2X AGP.

I am stuck at 640 x 480.

I have tried the xorg command to reconfigure the video card 4 times & selected the Intel i810 once, that was bad as I had to redo the xorg command thingy.
Good thing the terminal retains the prevoius commands!@

I am used to running a terminal in OS X but am diving into the Linux world on older PC's I have retained from friends.

Any help on how to install drivers? or reconfigure my system to work at higher resolutions would be greatly appreciated.

Thanks,

Marc

---

