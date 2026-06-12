---
title: "Nvidia drivers not working :("
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by Ratsock on 2007-10-20
Hi all,

I've recently come across a problem with my nvidia drivers. When starting up the OS I see the ubuntu loading screen and the little orange bar going side to side but after that the screen just goes blank. The OS is still loading correctly because I can hear the loading sounds, etc.

I do ctrl+alt+f1, then run dpkg-reconfigure xserver-xorg then ctrl+alt+backspace but no settings work for me (nv or nvidia). The only one that works is vesa and that has a pretty crappy resolution. 

Another strange thing that happened is that the last time I booted up and switchd to vesa when it wasn't working, it seemed to be really using the nvidia drivers... In the restricted drivers manager, it said "inuse" but the "enabled" chekcbox wasn't ticked. Im afraid to reboot again :P Unfortunately I cant run compiz because it thinks the drivers are not in use and tries to make me install them and reboot.

Before anyone asks, I have the latest nvidia drivers and my hardware is compatible as it was working fine before I reformatted and this problem came up.

---

### Post by asbani on 2007-10-20
Did you install a fresh new gutsy 7.10 or did you just upgrade? This problem has happened for me once, but that was on the gutsy beta and only for a short time, when I couldn't upgrade my restricted driver, but then An update for the "Restricted Driver" Happened in the update manager, and after updating it I got my problem fixed. another solution you can try is going back to an older kernel, and install nvidia driver from the nvidia website. 

goodluck.

---

### Post by Ratsock on 2007-10-21
I tried both :\
I did an upgrade and it didn't work, then I tried a fresh install too and it was still broken...

---

### Post by PmDematagoda on 2007-10-21
What is the error you face when starting X-server using the Nvidia drivers?

---

### Post by tripplep on 2007-10-21
Hello,

Sort of the same problem. I could only boot in a crappy 640x480 resolution. The restricted driver was enabled but didn't work.

My solution.
First check if Grub is loading the right kernel. I choosed to remove the old kernels when upgrading but for some reason they remained in /boot. 

I have two partitions, one with my work version (hda2) of ubuntu feisty (which I upgraded). And one test partition also with feisty (hda3).

I found out that grub was booting from hda3 with a untoched menu.lst and booted my previous kernel on hda2. My previous (old) kernel didn't work with the restricted nvidia driver. The solution was to change the menu.lst on hda3 to point to the right kernel (2.6.22-14). this solved my nvidia/geforce4 problem.

Hope this solves your problem too.

---

