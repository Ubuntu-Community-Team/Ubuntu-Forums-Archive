---
title: "Frequency out of range??"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by Dracus124 on 2008-09-29
Sorry if this is posted in the wrong area!

I installed drivers for my graphics card (nVIDIA GeForce6150LE) and when I start Ubuntu, It goes to the log in screen just fine, but when i log in, the monitor goes black and says "Frequency out of range."
I think I need to change the refresh rate or something, but I can't do it with because the desktop won't show up on the monitor?

Help!! Thanks!

---

### Post by Dracus124 on 2008-09-29
Bump

---

### Post by anystupidname on 2008-09-29
When you get the out of range message, try pressing CTRL-ALT-F1. 
A)If that doesn't work skip to B)
Then login and
```
sudo su
cp /etc/X11/xorg.conf /etc/X11.conf.broken
dpkg-reconfigure -phigh xserver-xorg
```
stop here

B)you'll have to boot to a liveCD, mount your hard drive, and
```
cp /<mountpoint>/etc/X11/xorg.conf.failsafe /<mountpoint>/etc/X11/xorg.conf
```

These are only stop gap measures to get you back in the GUI. You'll still need get your driver / video card setup to your liking after. If you'd like further assistance, state what you intend to accomplish and provide copies of xorg.conf, lshw -C video, and /var/log/Xorg.1.log or whatever else would be useful...

---

### Post by cariboo on 2008-09-30
If you are running hardy, in a termianl type:

```
sudo displayconfig-gtk
```

This should setup /etc/X11/xorg.conf with th proper modlines for your monitor.

Jim

---

