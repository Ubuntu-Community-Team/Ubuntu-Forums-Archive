---
title: "Blank screen after grub load on boot up"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by muerdeme on 2007-05-07
In order to get LiveCD to load without a blank screen, I had to remove the "splash" and "quiet" tags from the boot command.  I installed version 7.04 and it seemed to go ok, though there might have been a hangup at the very end... Now it starts to boot but goes to a blank screen after the grub loading text pops up.  I can hit escape and get to a command prompt.  I thought it was a video driver problem, but I've tried changing the driver in the X11 config to both ATI and vesa to no avail.

System Specs:
Ubuntu 7.04 on clean system
Install partitioned 200gb WD hard drive
2 gb DDR
AMD 64 bit 3700+
ECS RX480-A motherboard
DVD-Rom drive
**EDIT** ATI RADEON X800 XL video card

I can give any details from my xorg.conf file, but I don't have a way of copying it to a computer I can access the forums with.

Any ideas?

---

### Post by Sladi on 2007-05-16
Ati's newest drivers should be compatible with the 2.6.20 kernel but performance is horrible. :P

---

### Post by Sladi on 2007-05-16
sorry

---

