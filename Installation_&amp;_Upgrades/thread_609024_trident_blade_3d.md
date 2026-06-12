---
title: "trident blade 3d"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by odindio on 2007-11-10
I installed ubuntu (gutsey gibbon) and my video worked fine for 2 weeks.  I've had to reinstall.  Now every time I try to install - eventually I have a very poor resolution 600x800.  Initially I have good resolution - especially when I'm running the live disc.  I can't find a driver for linux.  And I can't adjust the resolution.  Is ndis wrapper a potential solution, or is there some other attempt I can make.

---

### Post by Nano Geek on 2007-11-10
Are you talking about a game or your screen resolution?

---

### Post by odindio on 2007-11-10
resolution, I can't even get my windows to fit on the screen anymore.  All my resolution.

---

### Post by Nano Geek on 2007-11-10
Try running this and see if it helps.```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by odindio on 2007-11-10
thanks, that fixed my problem.  I really appreciate your help.:):)

Maybe you know the answer to the last problem I had.  I actually reinstalled to fix this, but who knows it may happen again.  Everytime I logged in my keyboard stopped working.  I could use the keyboard to switch over using my kvm to my windows PC, but I could enter no text subsequent to logging in to unbuntu.  Or maybe you know a script, or something to check.  I did check in the keyboard settings (via the desktop GUI) - nothing there to be fixed. In addition,  I could type text into the xp machine.

---

### Post by Nano Geek on 2007-11-10
Any time. :KS

---

### Post by odindio on 2007-11-12
This fix was only temporary.  The problem came back.  I had to execute that sudo command several times.  Now it no longer fixes my resolution.

---

