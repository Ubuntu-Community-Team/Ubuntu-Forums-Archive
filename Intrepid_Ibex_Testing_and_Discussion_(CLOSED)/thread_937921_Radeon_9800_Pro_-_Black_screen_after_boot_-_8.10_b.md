---
title: "Radeon 9800 Pro - Black screen after boot - 8.10 beta"
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by War3333 on 2008-10-04
I have booted from the beta livecd correctly but after the installation I keep to get a black screen right after boot.

Every service and the machine itself seems to work.

Here Xorg.0.log:
[http://pastebin.com/m2d740d37](http://pastebin.com/m2d740d37)

some hints?

---

### Post by overdrank on 2008-10-04
Moved :)

---

### Post by ba5e on 2008-10-04
I am getting the same problem, but when booting the LiveCD. I hear the login sound play on the livecd but my monitor is in 'powersave' mode using the beta ISO. I have a x1950Pro connected by DVI, have tried using 'safe graphics' mode at the livecd menu, but no luck. I will go and get my xorg log file and post it here.

---

### Post by focamonje on 2008-10-06
I have the same problem and I have the Ati Radeon 9800 pro too...
Any solution?

---

### Post by otherush on 2008-10-06
Unlike the OP I haven't been able to successfully boot the live cd w/ my 9800 pro. Startup music plays but there are no visuals.

I installed using the alt. installation cd to see if I could configure xorg.conf later via the terminal. No luck, so here I am. :)

---

### Post by War3333 on 2008-10-09
I found a little workaround :), use the VGA port (I'm lucky that my monitor has both ports) the DVI exit doesn't seems to work in X.

---

### Post by otherush on 2008-10-09
I've been using the vga connection the entire time but I'm glad that worked for you war3333.  

I did manage to edit the xorg.conf file to the point that the versa drivers load.  Now I'm just waiting on fglrx drivers from ati that are compatible w/ this version of x.org.

---

### Post by UbuWu on 2008-10-09
Did you file a bug?

---

