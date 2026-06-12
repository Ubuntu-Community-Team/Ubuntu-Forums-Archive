---
title: "Ubuntu wont fresh install on new comp"
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by gamersino on 2008-07-01
So i just bought a new computer with these specs...
Intel q9450
2x 8800gt
4gb ram
780i motherboard 
2x 500gb hard drives 
and other unimportant things...
So when i try installing ubuntu (7.10 CD from Canonical) it goes fine till it hits 

*running local boot scripts (/etc/rc.local)                      [ok]

and after that it just stops... I tried checking the other threads but it looked like most hanged after they already had ubuntu installed... but this is a completely brand new install. Plz help!!!

---

### Post by mikewhatever on 2008-07-01
The first thing to do should be to check the live CD for errors. There is an option to do it on the very first screen presented.

---

### Post by avtolle on 2008-07-01
As I recall, 7.10 had a problem with IDE drive detection. You might want to edit the boot string and add all-generic-ide at the end of the line (before the -- at the end) and try to boot from there.

---

### Post by jualin on 2008-07-01
> **avtolle said:**
> As I recall, 7.10 had a problem with IDE drive detection. You might want to edit the boot string and add all-generic-ide at the end of the line (before the -- at the end) and try to boot from there.

To edit the line just follow this [link]("https://help.ubuntu.com/community/BootOptions"). Hope it helps!

---

### Post by gamersino on 2008-07-01
problem finally fixed... after finding this key combo (Ctrl+Alt+F1) when it hanged, i would type in sudo startx and everything went smoothly from there

---

### Post by jualin on 2008-07-01
Congrats pal, glad the problem is solved. Mark it as "Solved" using the Thread Tools on top of this page.

---

