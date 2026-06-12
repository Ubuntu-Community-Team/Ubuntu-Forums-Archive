---
title: "Intrepid Ibex alpha 6: Impressions"
date: 2008-09-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by PGHammer on 2008-09-28
Why would impressions of an alpha version of Intrepid Ibex (especially one which has issues with some Intel gigabit Ethernet cards) be worth your attention?  Largely because this is the first Ubuntu with the latest version of X (X.org 7.4/X server 1.5.1), which means there is actually less reason to use proprietary drivers for graphical support (X.org 7.4 includes 3D/DRI support for most AMD graphics chipsets, nV chipsets, and even Intel desktop/notebook graphics chipsets, especially the particularly persnickety R5xx/RV5xx from AMD).  In fact, it works out of the box (the issues I'm largely dealing with are the fault of my *monitor*, which is an older non-PnP CRT)!  Once they solve the teething issues typical of new builds, this will doubtless be another winner.

---

### Post by jerrylamos on 2008-09-29
Alpha 6 Ubuntu freezes up on this IBM Thinkpad R31, 32 bit 1 gHz Celeron, Intel graphics.  Linux can boot up all the way as verified in recovery root prompt, being command line functional.

X starts with movable pointer.  Then when Gnome 2 tries to load the first screen, the background, Alpha 6 totally locks up, freezes, won't do a thing except power off.  It's so dead it can't even post any messages or debug info or logs.  See bug 259385. 

Alpha 5 runs O.K. (that's what I'm using here).  

Xubuntu comes up O.K. without the freeze, however Alpha 6 Xubuntu Firefox 3.0.3 has some serious problems that Alpha 5 didn't:
1.  Firefox on Alpha 6 Xubuntu starts out O.K. then runs gradually slower and slower, finally won't even close.
2.  Firefox fonts on Alpha 6 Xubuntu start out O.K. then the characters gradually get polluted with extra pixels or missing pixels to the point of being unreadable.

If I can get Firefox to close, then restarting it is O.K. for a short time before it starts to degrade again.  I wonder if it is filling up memory and/or cache with junk.

Hope to see if the Beta on Thursday is changed 

Jerry

---

