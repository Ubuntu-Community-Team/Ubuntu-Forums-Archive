---
title: "Beginner having install trouble"
date: 2020-09-12
forum: Installation &amp; Upgrades
---

### Post by ouchthats on 2020-09-12
I'm trying to install Ubuntu server 20.04 on a machine I plan to use as a NAS. I've made a live usb, but starting up with it doesn't bring up an install menu; it doesn't seem to do anything. This doesn't seem to be entirely a problem with the usb, since it gives the install menu on a different machine. And it doesn't seem to be entirely a problem with the machine, since I can get the problem machine to start from a FreeNAS live usb. I'm quite a beginner, and I don't know what might be going wrong. Does anyone have an idea what might be going on, or what I might try?

Edited: Now I've got it recognizing the usb (although I have no idea how I did this) and bringing me to an install menu. However, when I choose "Install Ubuntu server", the screen just goes blank. So I'm still stuck.

---

### Post by TheFu on 2020-09-12
Which GPU?
Does a desktop ISO work at all?

---

### Post by ouchthats on 2020-09-12
No GPU; the CPU is an Intel Avoton C2550. The Ubuntu 20.04 desktop iso  seems to do the same thing: I can get to the Ubuntu menu, but choosing  "Try without installing" just gives a blank screen.

---

### Post by TheFu on 2020-09-13
Ubuntu installers need a minimal gpu.  There are ways to install on systems without a gpu, but i don't know how.
I did not look up that cpu to see if it has an embedded gpu or not.  A prebuilt image to be cloned that uses a serial console is probably necessary.

---

### Post by ouchthats on 2020-09-13
Fantastic! I'm pretty sure there is no embedded gpu, so this fully explains it. Thanks a ton!

---

