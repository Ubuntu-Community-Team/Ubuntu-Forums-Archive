---
title: "Blank/purple screen after ubuntu 12.04LTS install reboot on Dell laptop"
date: 2012-12-21
forum: Installation &amp; Upgrades
---

### Post by Philley on 2012-12-21
Dear Ubuntu User(s),

Please can you help?

I tried to revive my old Dell laptop computer by installing Ubuntu 12.04LTS in place of windows XP. After installing and rebooting, the infamous black/purple screen appears. According to forums its to do with the graphics controller compatibility with the ubuntu OS.

I have already tried the suggestions of gaining access to the GRUB menu during bootup and changing within the parameters of "ubuntu, with Linux 3.2.0-35-generic-pae" where the line that begins with "linux/boot ...", and replacing the mode "quiet splash" with "nomodeset" but without success.

I also tried replacing the "quiet splash" mode with "radeon.modeset=0" mode and that worked but only are few times. The first time it worked and I managed to login to ubuntu, I performed the necessary updates and even changed the GRUB parameters permanently by replacing the "quiet splash" mode with "radeon.modeset=0" thinking that I have solved the problem. But unfortunately the black/pruple screen reappeared even with the "radeon.modeset=0" mode already set permanently (which was really odd!). Now even with the GRUB parameters switched back permanently to "quiet splash" mode in one of the rare successful login attempts I was never able to login again successfully using "radeon.modeset=0".

The Dell inspiron 1100 laptop consists of an intel celeron CPU, 2.20GHz, 32-bit OS type, 1 gigabyte RAM, 60 gigabyte hard disk, with a 15-inch monitor. The video type is a direct AGP integrated graphics, video controller is an intel UMA integrated, and graphics controller is an intel 845GX86/MMX/SSE2.

Using the ubuntu 12.04 LTS liveCD works fine on the laptop the blank/purple screen issue only occurs when installing the ubuntu permanently on the PC.

Thanks!

Philley

---

### Post by DrScum on 2012-12-22
I don't have a specific answer to your question, but from the specs you give according to my experience (4 Dell Laptops inspiron 1501 being the oldest all running under different Ubuntu flavors) you probably won't be happy with Ubuntu. I'd recommend using Lubuntu or Xubuntu desktop. 

In order to solve your problem with a pretty long shot I admit, I would download the Lubuntu iso and perform a clean reinstall. Once the desktop is up install the applications of your choice and give it a try

---

