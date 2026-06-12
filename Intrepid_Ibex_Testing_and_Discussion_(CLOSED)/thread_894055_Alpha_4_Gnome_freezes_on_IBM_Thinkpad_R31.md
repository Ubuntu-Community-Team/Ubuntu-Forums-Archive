---
title: "Alpha 4 Gnome freezes on IBM Thinkpad R31"
date: 2008-08-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2008-08-18
Alpha 3 ran O.K. (for an Alpha) on Thinkpad R31.  
Xubuntu Alpha 4 and Kubuntu Alpha 4 run O.K. (for Alpha's)

Ubuntu Alpha 4 boots up to brown screen with cursor, then freezes with dead keyboard and no desktop displayed.  

Investigating, took Ubuntu Alpha 3 at 20080812 which runs O.K. and put on 217 updates current for today, all except the 17 updates for Gnome.  Runs O.K. so long as I don't put on the Gnome updates for Alpha 4.

See launchpad [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257450](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/257450).

This bug investigation is rather laborious, involving install of Alpha 3, putting on updates except for whatever group I suspect like the Xwindow or whatever, then when it fails I have to start all over again with another install.

If someone knows which of the 17 updates are more suspect, let me know.

Thanks, Jerry

---

### Post by Nullack on 2008-08-19
Stick with it Jerry :)

Your doing good stuff with keeping your bug updated.

I know that a major gnome update is coming very soon as part of the gnome release cycle.

---

### Post by jepong on 2008-08-19
hi jerry

i'm also a R31 user... does the trackpoint/mouse problem fix in intrepid ibex? thanks

---

### Post by jerrylamos on 2008-08-19
> **jepong said:**
> hi jerry

i'm also a R31 user... does the trackpoint/mouse problem fix in intrepid ibex? thanks

Track point support on Intrepid Ubuntu Kubuntu Xubuntu is just as flakey as Hardy & Gutsy.  There is a workaround for Feisty.  Edgy and Dapper just didn't have a problem.  Ubuntu decided to change their software for some reason they have never explained.  They blame the hardware however XP, Edgy, and Dapper run Trackpoint just fine, so I blame the software.

I get around the probem by using a USB mouse on the R31.  It works fine.  Just don't touch the trackpoint if the cursor is anywhere near any of the four edges.

Jerry

---

### Post by jepong on 2008-08-20
hi jerry,

thanks for the infos.

hope by adding i8042.nomux=1 on grub still do the trick in intrepid

---

