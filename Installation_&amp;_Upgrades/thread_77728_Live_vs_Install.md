---
title: "Live vs Install?"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by mattack on 2005-10-17
At work I have a DELL Optiplex GX520. The only upgrade is the video card, which is a GeForce MX4000. I want to run Ubuntu Breezy. I tried the live CD to see if it would autodetect the hardware correctly but it could not configure the X Server correctly.
Am I safe in assuming that if I were to install Breezy, I would have similar trouble? I just want to know what I'm in for...
Thanks...

---

### Post by adwait on 2005-10-17
If the Live CD didn't have the correct drivers, you can safely (!!) assume that the installation CD will have the same problems too.

---

### Post by mattack on 2005-10-17
that's what i figured...
is there a (relatively) easy way get them?
can install normally, login to a console and apt-get the correct drivers?
or is there something i can do while installing to get them? apt-get reconfigure xorg.conf maybe?

---

### Post by adwait on 2005-10-17
Try this:
[http://www.ubuntuforums.org/showthread.php?t=52924&highlight=geforce+drivers](http://www.ubuntuforums.org/showthread.php?t=52924&highlight=geforce+drivers)

---

### Post by mattack on 2005-10-19
ahhh new thing...
a co-worker tried installing breezy on another computer (same model DELL). it mounted the hard drive then lost access to the CD drive...
weird.
anyone know why that would be and how to fix it? :)

---

### Post by baronKarza on 2005-12-12
same problem. I suppose it's a problem with sata controller.
I'm forced to use Fedora Core 4 (it installed without any problem...)#-o

---

