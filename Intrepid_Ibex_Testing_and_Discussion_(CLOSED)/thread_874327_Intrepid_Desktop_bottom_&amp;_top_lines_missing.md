---
title: "Intrepid Desktop bottom &amp; top lines missing"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jerrylamos on 2008-07-29
Xubuntu Alpha 3 Intrepid 8.10 installed & running, Xubuntu-restricted, updates, etc. was running O.K.

Firefox Yahoo video O.K.  Tried Yahoo.com video and window got stuck.  Close did not complete.  Did a restart, now the desktop background, mouse, & icons come up but not the top & bottom lines.  I can start a terminal.

Ctrl-Alt-F1, login, sudo killall GDM, startx gets it going again with complete desktop until I re-boot.  Then desktop background, icons, & mouse but not top & bottom lines.  Somehow a new boot keeps remembering something from the last boot instead of doing a full startx.

Any ideas on how to get Xubuntu desktop going again from boot?

Thanks, Jerry

---

### Post by Pumalite on 2008-07-29
Intrepid Ibex is in development.
You might try the sub-forum

---

### Post by overdrank on 2008-07-29
Moved :)

---

### Post by Gina on 2008-07-30
Yes, I think something got changed and now the system remembers the changed setup and that's now what you're getting.  You may need to renable the panels.  You don't say if you're running the 32 or 64 bit version of Xubuntu.  I'll be testing Xubuntu Alpha 3 shortly - I have both 32 and 64 bit systems.  I'll report what I find.

---

### Post by jerrylamos on 2008-07-30
Thanks, Gina, this is on the 32 bit Xubuntu Alpha 3 on a 1.2 mHz Celeron test system I use before hazarding Intrepid on my main system.  The test system is dual booted with Ubuntu Intrepid Alpha 3 which at the moment doesn't have the problem about "remembering" a defective desktop.  

I presume the cause is an interaction between Xubuntu and the ATI graphics chip and/or driver which may be responsible for the Firefox hangs; there should be a way to close Firefox get the desktop going clean again (short of another install!).

I would like to know how to boot with a "fresh" start in case of problems.  I've tried some of the logout/login choices with the same result every time.

If useful I can do a Launchpad bug with logs & lspci & such.

Thanks, Jerry

---

### Post by philinux on 2008-07-30
You could try deleting the equivalent folders to .gnomexxx in your home folder, whatever they are called in xubuntu.

---

### Post by jerrylamos on 2008-07-30
There is:
.gnome2
   accels     which is empty
   gnome-power-manager
   keyrings

.gnome2_private
   bookmarks.html  Documents   Music     Public    Templates
   Desktop         lspci-vvnn  Pictures  smb.conf  Videos

Poked around these - none seemed offhand to be useful for this problem.

Thanks, Jerry

---

