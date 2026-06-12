---
title: "Problems installing"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by ikak on 2007-10-06
I'm trying to dual boot with XP Pro.  So i burned the ubuntu CD, did a fresh install of XP just for fun.  Set it up with all my drivers on XP then went to start the ubuntu install. I got the first prompt to choose what i want to do so i chose Start Ubuntu.  It did its little loading thing then went to a completely blank screen.  I searched around here and found someone who had a similar issue and fixed it by pressing f6 and using the command 'linux vga=771'.  So i tried that, it started working (I didnt get the blank screen), but after it went a little further and stuff i got an error saying 'Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?'


Any ideas?

---

### Post by Pumalite on 2007-10-06
Try:

sudo dpkg-reconfigure xserver-xorg

---

### Post by ikak on 2007-10-06
No luck.. After I choose Start Ubuntu on the first menu of the CD it does the Ubuntu loading screen then goes completely blank.  Nothing at all.

---

### Post by Pumalite on 2007-10-06
Try Alternate CD

---

