---
title: "Ubuntu 10.9 Freezes After Installation"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by westfc91 on 2009-12-22
Greetings,

I'm trying to install Ubuntu 9.10 on my PC and am encountering some issues after installation. 

When I boot off the CD and select the option to install Ubuntu directly everything goes fine up until the point where I reach my desktop. My desktop will function normally until I perform an action such as opening a program or window of any type. When I do everything on the desktop freezes but my ability to move my cursor. After that I've noticed the whole des   ktop will beginto distort. The same problems occur while running Ubuntu from the live CD.

Here is an image of the distorted area:
[http://img35.imageshack.us/img35/2176/photoqc.jpg](http://img35.imageshack.us/img35/2176/photoqc.jpg)

I'm using a 32 bit PC with a 3.4GHz Intel P4 processor with 1GB or RAM and an Nvidia GeForce 7800 GT graphics card.

Any input on what could be casing this issue would be greatly appreciated!

Edit: I noticed the version number for Ubuntu in my title is incorrect. I meant 9.10.

---

### Post by lemming465 on 2009-12-24
Sounds like bugs in the video driver, alas.  Are you running the open source "nv" or the binary nvidia one?  Try the other one.  If you need 3D acceleration, you might have to install the latest binary beta directly from nvidia.com (you'll need to do *sudo aptitude update; sudo aptitude install build-essentials kernel-headers* first).

Reinstalling with an older ubuntu version such as 9.04 might give better results, ironically.  Definitely try a live CD of that before resorting to it.

---

