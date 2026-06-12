---
title: "Screen Resolution Stuck at 640x480"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by ZainZXC on 2006-08-31
Yeah the tittle sais it all... plz post back for solutions

---

### Post by croak77 on 2006-08-31
The title does not say it all. We need a just a little bit more info. What Xorg driver are you using? Do you have a video card? If yes, which one? What resolutions does your monitor/laptop support?

---

### Post by ZainZXC on 2006-08-31
Yes i do have a video card ~Nvidia GeForce 5200~ and my monitor can handle a 1024x768 resolution

---

### Post by mlind on 2006-08-31
Open a terminal and type:
```

sudo dpkg-reconfigure xserver-xorg

```
Accept the defaults until you get to choose display resolutions. Make sure you select desired resolutions. Then close all desktop applications and press Ctl+Alt+Backspace.

If you don't have more resolution options now (System > Preferences > Screen Resolution), change to [nvidia proprietary driver]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia"). If this doesn't help either, post your /etc/X11/xorg.conf

---

### Post by ZainZXC on 2006-08-31
Yeah thnx it worked!!

---

