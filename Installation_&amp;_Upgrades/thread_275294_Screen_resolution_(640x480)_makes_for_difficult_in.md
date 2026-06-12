---
title: "Screen resolution (640x480) makes for difficult install"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by wallyg on 2006-10-11
I would like to install, but due to limited screen resolution, I can not see the buttons towards the bottom of the screen.  I tried to re-size by using the "screen resolution" menu item, but only 640x480 option is shown.  I also tried the settings on my monitor, but with no luck. 

I also tried to re-size the "window"? but its size will not shrink so that I can see the buttons.

I try to tab (blindly) and this partially works, except when I get to choosing the time-zone screen, every time I try to tab and hit enter, I have to choose my city again.  At this point I can go no further.

Thanks in advance for suggestions,
Walt:-k

---

### Post by bigken on 2006-10-11
what type of video card do you have if you know which 1 you have in a terminal type sudo dpkg-reconfigure xserver-xorg and select your video 
type then when you get to the resolution sizes use the spacebar to select 
which 1s you want ;)

---

### Post by Kateikyoushi on 2006-10-11
Try to use the safe video mode or the alternate install cd.

---

### Post by Tunemonkey on 2006-10-11
I'm in the same boat as you Wally. I have a Powerbook and can't see enough to install, nor am I able to change the resolution from 640x480 to anything else. I went through and changed the xorg.conf file and saved, but still not able to change. 

It must be an issue with the graphics chipset which is this:


  Chipset Model:	ATY,RageM6
  Type:	Display
  Bus:	AGP
  Slot:	ATI
  VRAM (Total):	16 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4c59
  Revision ID:	0x0000
  ROM Revision:	113-XXXXX-115

If you come up with anything, please post. I'll do the same.

Rob

---

### Post by Kateikyoushi on 2006-10-11
Did you try it with a lower color depth ?

---

### Post by wallyg on 2006-10-11
bigken,

Thanks for the help.  I tried your suggestion, but it didn't work.

Wally

---

### Post by bigken on 2006-10-12
run command again and select vesa as your video card 

did you reboot ?

---

### Post by wallyg on 2006-10-12
I tried everything that people kindly suggested with no success.  I did get this from the linux forums website...

======
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

and then Rebooted the system.
======

I cut and pasted each line into the terminal, re-booted and it WORKS!  Thank goodness because I'm a real novice at this sort of thing.

Thanks to all who took the time to respond.

Wallyg

---

### Post by wallyg on 2006-10-12
I might add, that I bought a Linux magazine that featured Ubuntu and had all the install steps pictured so that I could install Ubuntu first before trying to do the cut/paste procedure.

---

