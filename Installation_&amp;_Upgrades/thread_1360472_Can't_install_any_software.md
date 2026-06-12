---
title: "Can't install any software"
date: 2009-12-20
forum: Installation &amp; Upgrades
---

### Post by otisranson on 2009-12-20
Hey guys, new to Ubuntu, not to linux.  I just installed 9.10 amd64 on my machine.  I had it earlier with a dual boot, but just decided that a full linux system is going to do what I need.  Anyway, in the software install center, I click on a package I want to install, and there's no install button in the description of the package.  I was able to install software under a previous install (amd64 edition as well), but now I can't.  Do I need to somehow update the software center?  Also, I have an nvidia card, but when I go to the hardware drivers, it's telling me no proprietary drivers are in use.  I haven't installed any of the nvidia drivers yet.  :confused:  Thanks for the help.  Sorry for the newb question. :KS

---

### Post by bboston7 on 2009-12-21
run ```
sudo apt-get update
``` in the terminal then try again.

---

### Post by otisranson on 2009-12-21
Thanks! Worked.

---

