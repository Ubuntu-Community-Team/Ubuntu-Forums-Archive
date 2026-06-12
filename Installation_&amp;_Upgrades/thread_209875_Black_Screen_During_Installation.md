---
title: "Black Screen During Installation"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by makan tai on 2006-07-05
Got my Ubuntu version 6.06 from ship-it, put in the cd, apperared to be installing until it got to the graphical interface part...then I get the black screen with a frozen cursor.  There's no way out of this other than turning of the computer.

I tried the safe graphics mode, and reconfigured the xserver as follows:

sudo dpkg-reconfigure xserver-xorg
  during reconfigure, I selected vesa, and after that not working, vga.

sudo dpkg-reconfigure gdm

sudo reboot

At this point, Ubuntu seems to shutting down, it ejects the cd and tells me to hit enter, after which it boots into windows. If I re-insert the cd and try to start Ubuntu, I get the black screen.

I have a Pentium III, and a Nvidia GeForce2 MX-200/400 graphics card.  Windows is on its own drive.  Any ideas?

---

