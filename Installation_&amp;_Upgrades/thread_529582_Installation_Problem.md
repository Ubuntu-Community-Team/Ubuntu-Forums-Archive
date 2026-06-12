---
title: "Installation Problem"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by robertfdawson on 2007-08-19
Laptop: HP NW8440 w/ATI firegl v5200 VGA. 100GB SATA HDD running XP PRO SP2. Have internet access.

When I boot to the UBUNTU 7.04  live CD, X will not start. I found a post that suggested I do the following (with my ethernet cable plugged in for internet access).

Drop to Shell Prompt: SUDO -S
APT-GET UPDATE
APT-GET INSTALL FGLRX-CONTROL
DPKG-RECONFIGURE XSERVER-XORG
skip auto detect accept defaults select fglrx as VGA settings of 1680 x 1050 @ 75HZ and then  medium det.

Then I typed STARTX and it booted to the live CD. The live CD then works great with proper display and internet access. I need to know how do I install 7.04 with the above limitation. Preferably in GUI mode.
Can I install it while the live cd is running? If so what are the steps.
At the point that I typed STARTX should I have issued a different command to begin the installation in GUI mode?
 Please be detailed since I am not very experienced in command line. 

Thanks,
Robert

---

### Post by forestpixie on 2007-08-19
once you've got the livecd running - the install icon should be on the desktop

---

### Post by robertfdawson on 2007-08-19
I did not see it, but i will look again. There is no install icon on the desktop. Probably because of how I had to start it???? Any other ideas? Do you know another way to start it?

---

### Post by Pumalite on 2007-08-19
Try Alternate CD. Avoids graphical interface problems. (Text Mode)

---

### Post by robertfdawson on 2007-09-09
There is no installation icon on the Desktop. While waiting I downloaded PC Linux OS 2007. It works properly as is. I installed it and have been using it ever since. Try it out. It has a very appealing appearance.

---

### Post by Pumalite on 2007-09-09
I use it. It's great, as is LinuxMint and Mepis that I also use. Viva Linux

---

