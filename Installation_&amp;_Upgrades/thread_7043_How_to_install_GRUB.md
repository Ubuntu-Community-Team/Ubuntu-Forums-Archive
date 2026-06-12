---
title: "How to install GRUB?"
date: 2004-12-03
forum: Installation &amp; Upgrades
---

### Post by Berkut on 2004-12-03
I had to update windows. So GRUB is overwriten. There are many threads in the forum about GRUB but I don't find how to install it again. I am a noob in linux and can't help myself with the GRUB homepage. 

So preety please if someone can post a step by step install for it (I think my disk is hds), as I was really working hard the last weeks to get ubuntu up and runing with the help of this great forum (ATI 3D acc, Mplayer...), but windows offcourse doesn't mind other OS's. :sad:

---

### Post by jdong on 2004-12-03
ok, first, get a rescue CD or live CD. If you have a copy of Knoppix, use it. Otherwise, grab SystemRescueCD and burn it.

Get the a root prompt. (In Knoppix, start up a console, type **sudo su**). Systemrescuecd will boot directly to a root console

Type in **grub** to launch grub. Type in **root (hd0,0)** to tell GRUB where your Linux boot partition is. Replace the last 0 with the partition number (type in [b]root (hd0,<TAB> to get a hint).

Type in **setup (hd0)** to install GRUB. Reboot.

---

### Post by Berkut on 2004-12-04
Many many thanks jdong. It worked right away with an old knoppix CD.  :mrgreen: 

To this date I have tried 4 other linux distributions, but Ubuntu realy is the most user friendly. If not the distro, the forums make it realy stick out off the crowd!

---

