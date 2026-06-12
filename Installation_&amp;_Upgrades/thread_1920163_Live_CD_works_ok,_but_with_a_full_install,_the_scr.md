---
title: "Live CD works ok, but with a full install, the screen gets all messed up."
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by Shunt1984 on 2012-02-04
I downloaded Ubuntu 11.10 and before I installed, I tested it first in a live session to see if everything worked ok. It did so I proceeded to do a full install.

When I boot up, the screen shifts to the right and I can't even see the menu bars or the Unity bar, just the wallpaper and the mouse (I can't click anything because there is nothing to click). 

I also tried to boot in recovery mode but happens the same thing, the command line appears at the middle of the screen instead of appearing on the left side...

I'm thinking that it's something about the drivers, because in the live session, the generic drivers are used, am I right? Is there any way to keep these drivers in the full install?

My graphics card is an ATI Radeon HD 6850.

Thanks!

---

### Post by raja.genupula on 2012-02-04
...did you got anything when you press alt+f2. 

...open your terminal and post the output of **lspci** and paste here .

---

### Post by Quackers on 2012-02-04
Have you tried the nomodeset boot option?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

