---
title: "Installing Nvidia GT 240"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by orange2k on 2012-10-22
I have a problem with the Nvidia GT 240 graphics card: I cannot boot with it - it shows strange artifacts on screen after GRUB...
I also have some onboard Nvidia graphics card that uses shared memory and thats the only thing that allows me to boot into Ubuntu - I have a dual boot system and Windows has no problems with GT 240, only Ubuntu. Thus, every time I want to start Ubuntu, I have to go into BIOS and enable my onboard graphics card, unplug the monitor, plug it into the onboard graphics card and reboot.

Has anyone had the same problem? 
Is there a workaround, so I can install and enable the proprietary Nvidia drivers for GT 240 without booting into Ubuntu, the CLI way?

edit: I installed Ubuntu 12.04 64-bit

---

### Post by dino99 on 2012-10-22
are you using the latest nvidia driver from xorg-edgers ppa ? if not, then you should.

---

