---
title: "Installation problem on Sony Vaio"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by loboes41 on 2007-10-01
I just installed Xubuntu to my old Sony Vaio PCG FX-220 via the alternate install cd. When I boot it up now, I see GRUB 1.5 loading, then text that says "loading" and then the screen turns black and stays that way, no matter how long I leave it. 

I figured out that if I press Alt + F1 during this time, I can see the boot process. The first thing that comes up is: "usplash:setting mode 1920x1440 failed" and repeats that message for 3 more different resolutions. Then it continues booting, until i get to a command line.

Does anyone have any ideas what I can do about this?

---

### Post by Pumalite on 2007-10-01
Try:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx

---

### Post by loboes41 on 2007-10-01
Thanks!

X server loads now, but there is still the 3 inches of black space around the edges of the laptop screen.  

I tried reconfiguring xorg.conf a few different times, and got it slightly larger once, but can't figure out how to fix it.

---

### Post by Pumalite on 2007-10-01
You must have some hardware controls for your screen. At least monitors do.

---

### Post by loboes41 on 2007-10-02
The only control I can find is to change the brightness of the screen.  I've tried pushing Fn + every other key on the keyboard.

---

