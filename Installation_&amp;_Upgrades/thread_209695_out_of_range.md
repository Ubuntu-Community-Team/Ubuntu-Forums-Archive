---
title: "out of range"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by Cai876 on 2006-07-05
i am only a noob with linux (first time ever to install) and i am in need of some help. 
when i boot from the instalation cd i click install then it lists everything aned sais ok but then the screen goes black and a mesage sais out of range.
i have a 9200 256mb ati card.

plz help
cheers
cai

---

### Post by Dr. Nick on 2006-07-05
Is this the live cd?

It sounds like it is not picking up your videocard/monitor correctly. If you are trying to boot the live cd hit "start ubuntu in safe graphics mode" and see if that helps,

If you are using the alternate install cd and got through the installation process and it errors on reboot then you need to run

** sudo dpkg-reconfigure xserver-xorg** and pick the correct monitor type.

---

### Post by Cai876 on 2006-07-05
i am using a cd that i burnt my self from the iso on the website.

---

### Post by Dr. Nick on 2006-07-06
The desktop, or alternate cd?

If you could just clarify abit at what part you get the "out of range" message it may help some.

If I am thinking of the right thing the message isnt generated bu ubuntu, but your monitor. This error is usually caused by the refresh rate or screen res. being outside of the monitors capabilities. 

Knowing which iso and exactly where the error occurs will help determine which of the 2 above suggestions you should use.

---

