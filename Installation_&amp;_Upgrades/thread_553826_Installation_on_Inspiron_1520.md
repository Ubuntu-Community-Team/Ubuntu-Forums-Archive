---
title: "Installation on Inspiron 1520"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by vav on 2007-09-18
After install issues, I finally installed a base system from text mode and then changed sources.list to network sources, and manually did 
apt-get install ubuntu-desktop

After changing to the new intel driver, everything seems to work, but a few things:
1> I dont have man pages in my gnome-terminal !
2> My screen looks faded and blurry... the background is sharp, but text and graphics rendered otherwise are grainy looking. I suspect the color depth is low (the ubuntu login screen shows ellipses instead of a smooth gradient), although the default in xorg.conf is 24. I have the resolution set to the screen's full 1440x900... what else could change the color depth?

What to do?

Thanks!

---

### Post by Pumalite on 2007-09-18
Install proprietary driver if you have appropriate video card.

---

### Post by vav on 2007-09-18
I already have the 
xserver-xorg-intel
driver... and intel graphics. So I assume there's no other proprietary driver...?

---

### Post by Pumalite on 2007-09-18
There is this:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

