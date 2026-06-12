---
title: "Gutsy Kubuntu wont upgrade or install new programs - no adept"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by Richard Perry on 2007-11-29
I have just installed Kubuntu Gutsy.  I had Feisty previously.  Feisty would not update or upgrade.  I would get kicked out of adept.  I then formatted the drive and installed Gutsy from CD using the whole disk.  It is a dual system with Windows on the first drive and linux on the second.  I was able to add Firefox from the adept GUI.  After that adept simply crashed when I tried to run it from the menu.  

Gutsy runs fine except for this small problem.  I would like to be able to add programs and upgrade from time to time.

I have gutsy on a laptop which does not have this problem.

---

### Post by kle on 2007-11-29
Yes, I recognise this one. 

Go to terminal and write: sudo dpkg --configure -a
enter
exit
Then try again. 

Good luck

---

