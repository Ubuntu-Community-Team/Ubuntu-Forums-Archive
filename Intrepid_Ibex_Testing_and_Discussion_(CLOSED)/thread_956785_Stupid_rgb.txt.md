---
title: "Stupid rgb.txt"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bexamous on 2008-10-23
Where is this file supposed to come from?  Its gone in ibex.  Conky flipped out so I just used sed to get rid of color names and replaced with numbers.

Now emacs won't run.  ARGH.

There is a symbolic link /usr/share/X11/rgb.txt to /etc/X11/rgb.txt which doesn't exist.

Other than that nothing.

x11-common is installed, and reinstalled.
xrgb package no longer exists.

This is driving me nuts how simple this should be.


Even if I just copy an old rgb.txt file from another system to /etc/X11/rgb.txt still nothing works.

bexamous@nine:~$ emacs
Undefined color: "black"
bexamous@nine:~$

---

