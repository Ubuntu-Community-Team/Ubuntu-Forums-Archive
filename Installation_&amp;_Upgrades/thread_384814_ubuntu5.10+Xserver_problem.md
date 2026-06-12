---
title: "ubuntu5.10+Xserver problem"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by karanj on 2007-03-14
Hi

I am new to linux....blah blah...

I have a compaq 3230au notebook with nvidia GO 6150 graphics....During the installation i get the message:

"Failed to start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem"

Would anyone have a clue to solving  this one??? :confused:

---

### Post by zvacet on 2007-03-16
ctrl+alt+F1
```
 sudo dpkg-reconfigure xserver-xorg
```
If your graphic card is set as nvidia try nv

---

