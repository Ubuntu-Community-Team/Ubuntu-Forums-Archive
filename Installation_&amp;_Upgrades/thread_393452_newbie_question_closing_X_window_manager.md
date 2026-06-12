---
title: "newbie question: closing X window manager"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by ThumbBumpkins on 2007-03-25
i am trying to install beryl, and i am currently trying to install the latest nvidia drivers. however, i can't figure out how to close X so that i can install the drivers. i tried 

sudo /etc/init.d/gdm stop

per the beryl installations wiki's instructions, but that just took me to a blank black screen with no prompt and none of my commands execute. is there an easier way (or a way that actually works) of closing X but still having a working prompt?

---

### Post by NT4usB on 2007-03-25
Ctrl+Alt+F1
login 
then sudo /etc/init.d/gdm stop

---

