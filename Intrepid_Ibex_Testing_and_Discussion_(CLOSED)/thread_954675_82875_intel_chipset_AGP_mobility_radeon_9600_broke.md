---
title: "82875 intel chipset AGP mobility radeon 9600 broken fglrx"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2008-10-21
sorry but fglrx says no devices detected and forces a startup in low graphics mode.

---

### Post by kngunn on 2008-10-21
Similar problem for me.  Nothing but text mode, though.

Mine's a Lenovo ThinkPad T500 with an Intel GMA 4500HD ATI Mobility Radeon 3650.

My understanding is that Ibex *should* automatically roll over to the Open Source drivers since the proprietary ones won't work.  Didn't happen.

Saw that the new ATI drivers should be in the repository today, but those aren't working for me either.

I'm trying RadeonHD next (after another fresh install just to have a clean starting point).

---

### Post by sdowney717 on 2008-10-21
Bump, fglrx does not detect my ATI AGP radeon 9600 se 64mb mobility video card.
Any ideas?

this seems to be an issue with this intel server  Motherboard Model -- Intel Entry Server Board S875WP1-E. and the 82875 chipset as I tried an x1300 256 radeon and get the same thing.

---

### Post by kngunn on 2008-10-22
Solved for the T500:

> **kngunn said:**
> Similar problem for me.  Nothing but text mode, though.

Mine's a Lenovo ThinkPad T500 with an Intel GMA 4500HD ATI Mobility Radeon 3650.


The ThinkPad T500 has DUAL graphics graphics attached to a single display.  In the BIOS you'll find a display setting for "switchable", "discrete" or "integrated" and one to determine whether or not this should be detectable by the OS.  You need to turn OFF detectable and change "switchable" to "discrete".  Yesterday's Ibex daily (with the new fgrlx driver in it) now works like a champ.

That's why my adapter info looked so odd -- it's two cards.  Anyway, everything now looks great.  Hope this helps someone else!

---

