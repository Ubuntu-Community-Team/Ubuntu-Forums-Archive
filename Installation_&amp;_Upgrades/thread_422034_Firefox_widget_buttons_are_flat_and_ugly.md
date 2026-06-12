---
title: "Firefox widget buttons are flat and ugly"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by shirsch on 2007-04-24
Title says it.  For reasons unknown, Firefox 2.0.0.3 on my Edgy 32-bit system is rendering buttons and text entry fields on dialog boxes (e.g. file selector) "flat".  When pushed, buttons sink below the surface.  Appearance of both these and text entry fields is incredibly ugly.

If I run a 64-bit Firefox using the same personal settings directory, it renders properly (buttons slightly raised, depress below surface when picked on).  I've exhaustively compared every other directory associated with Firefox configuration between the two machines and cannot find any differences to account for this.  I'm starting to suspect something to do with gtk, but thought I'd ask if anyone has seen this before flailing around further.

Update:

Solved the problem by running strace on both boxes, sorting and comparing the files they open.  Then iterated in line-by-line until things fixed themselves.

In ~/.qt/qtrc, the following line:

style=keramik

needed to be changed to:

style=Plastik

I have absolutely no idea how this was changed, nor why the 64-bit version of Firefox didn't pay attention it.  However, all's well that ends well - the widgets are back to normal again.

---

