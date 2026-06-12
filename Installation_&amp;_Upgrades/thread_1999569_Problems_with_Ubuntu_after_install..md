---
title: "Problems with Ubuntu after install."
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by jjd712 on 2012-06-08
i just installed Ubuntu 12.04 and the install went good. but after a reboot i get this screen with a bunch of horizontal lines across the screen. is this a driver error, or a bad install?

[http://img232.imageshack.us/img232/7164/imag0121ri.jpg](http://img232.imageshack.us/img232/7164/imag0121ri.jpg)

---

### Post by dino99 on 2012-06-08
first check the driver activation, into a terminal, run:

sudo jockey-gtk

and be sure there is no xorg.conf around, run into a terminal:

sudo rm /etc/X11/xorg.conf*

then logout/in

---

### Post by jjd712 on 2012-06-08
> **dino99 said:**
> first check the driver activation:

sudo jockey-gtk

and be sure there is no xorg.conf around:

sudo rm /etc/X11/xorg.conf*

then logout/in


:shock:i have no clue what you just said... im a complete noob, this is my first time installing Linux. well any os other than windows for that matter.

---

### Post by dino99 on 2012-06-08
> **jjd712 said:**
> :shock:i have no clue what you just said... im a complete noob, this is my first time installing Linux. well any os other than windows for that matter.

open a terminal (ctrl+t) to run the given commands posted above

---

### Post by jjd712 on 2012-06-08
ok. After attempting to open a terminal it won't open pressing ctrl+t. do you want a video of the start up?

---

### Post by jjd712 on 2012-06-08
Problem is defently a driver problem, i removed my gtx 560 ti 448 and ubuntu booted up with out a problem on the intel iGPU

---

