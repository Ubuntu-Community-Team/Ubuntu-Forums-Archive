---
title: "xubuntu installation mouse and X server problems"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by pdc124 on 2007-10-04
iim just installing Xubuntu on an older (450MHz)  machine . FWIW DSL works well so im just  want to see what i can install 
I get a GUI from the liveCD , but the ps2 mouse isnt recognised. 
problems 
1 mouse 

running dkpkg-reconfigure  gives me an option for the screen resolution  - when i  select what i want and press return it  says it waves it and then drops to the console.

the  installed xorg.conf has the mouse device as /dev/input/mice 

in /dev/input ive got 
/dev/input/mice and 
/dev/input/mouse0

cat /dev/input[mice|mouse0] gives me no screen output 

in addition ctrl-alt-backspace switches my machine off ( immediately - ie kills the power , not a shutdown routine) 
so i cant restart the GUI having edited xorg.conf 

the mouse problem seems to be reported before but i cant find a definitve solution 

and restarting the GUI ????

---

