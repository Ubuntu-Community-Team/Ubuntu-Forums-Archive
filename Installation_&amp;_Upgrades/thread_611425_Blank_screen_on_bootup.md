---
title: "Blank screen on bootup"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by ikt on 2007-11-12
Hi,

I have another computer, fairly old video card and LCD monitor.

If I boot the computer up on a CRT monitor, it boots fine, 1024 x 768 is the screen resolution, everything is great, however if I plug in the LCD monitor it shows nothing.

If I plug back into the CRT and set to 800 x 600 then switch over it works, I can also then change to 1024 x 768 and it will still work.

However when I reboot again it shows a blank screen 

Any advice?

---

### Post by confused57 on 2007-11-13
> **ikt said:**
> Hi,

I have another computer, fairly old video card and LCD monitor.

If I boot the computer up on a CRT monitor, it boots fine, 1024 x 768 is the screen resolution, everything is great, however if I plug in the LCD monitor it shows nothing.

If I plug back into the CRT and set to 800 x 600 then switch over it works, I can also then change to 1024 x 768 and it will still work.

However when I reboot again it shows a blank screen 

Any advice?
If I understand correctly, you can boot using the LCD monitor after changing the resolution to 800 x 600 while connected to the CRT & rebooting with the LCD connected..  If this is the case, have you tried:
```
sudo dpkg-reconfigure xserver-xorg
```
in a terminal after reconnecting the LCD monitor...select "Yes" at the first screen to "autodetect" your hardware...you can also select what resolution(s) you want to use.

---

