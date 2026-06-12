---
title: "Installing 32bit ubuntu on 64bit system"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by carsten on 2006-12-23
Hi
Since there are much more software for 32bit systems, and much less problems, I was wondering if it was possible to run a 32 bit ubuntu on my 64 bit system.
I tried it once (1½ year ago) but I got annoying clock problems(time passing twice as fast), fixed it by getting a new kernel, but then my video card didnt work anymore, so before i try it, i want to make sure that it is even possible. (Although strange, there was no clock problems while on the livecd.....)

My system:

Acer Ferarri 4000, AMD Turion 64, ATI x700

---

### Post by bulldog on 2006-12-23
Should be fine.
It's possible you're getting some trouble with your ATI card,but on the other hand if it runs fine on the live cd,it should do after the install.

---

### Post by gonesolo on 2006-12-24
32 bit will work fine on a 64 bit machine. just a word of warning however regarding your ATi card. not sure if the X700 is supported by the radeon driver, if it's not when the install is complete you'll see a black screen (possibly your monitor will give you a display out of range message)

If it does switch to a console (CTRL+ALT+F1 I think) and type the following

sudo nano /etc/X11/xorg.conf

Find the line that looks like this

Device "radeon"

and change it too

Device "vesa"

Press CTRL + X and select yes to save (using the same file name)

Then type 

Sudo reboot

and you should be good to go next boot up.

---

