---
title: "[SOLVED] No display after usplash"
date: 2008-07-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Lem on 2008-07-26
Tried an upgrade from Hardy, and then a fresh install of Intrepid Alpha 3 on a spare machine.
On both occasions, I get a strange second taskbar on the usplash and then the display goes blank. The monitor is still receiving a signal, but a can't see anything . alt+f1 doesn't change things either.

It's a bog standard intel 945 chipset running into a 17" bog standard 4:3 ratio monitor. Nothing exotic whatsoever. Runs Hardy perfectly.

Seems like a framebuffer issue. Anyone else had this?

---

### Post by autocrosser on 2008-07-26
There have been problems with Usplash this cycle--take a look at:  [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/249037](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/249037)

For one of them--if you browse LaunchPad bugs--you wiil find more--I've posted several of them....seems this is happening with Intel & certain Nvidia chipsets.

Are you ending with GDM & a viable Gnome session?

---

### Post by Lem on 2008-07-27
No.. that's the point. I get no GDM - just a blank screen. I can log in using my user/pass and the hdd whirrs away but still nothing. I can't even pull up a console.

---

### Post by Lem on 2008-07-27
Jumped into the recovery console at grub and ran xfix. All is ok. My x must be getting misconfigured during install.

---

