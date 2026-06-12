---
title: "Xserver error upon startup cannot boot"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by jamienos on 2007-08-05
I was manually editing my xorg.conf file and i seem to off messed it up somewhere..

Try to boot up into ubuntu feisty, i get a nice welcome xserver error stating one of the lines under  monitor in /etc/X11/xorg.conf is wrong or something like that the ver refresh type settings i think and also claim's there is no screen

Is there anyway i can get it back or reset the xorg.conf or anything like that?

thanks

---

### Post by merlinus on 2007-08-05
Ctrl-Alt-F1 to get to prompt (if you are not already there).

sudo dpkg-reconfigure xserver-xorg

Then:

startx

-merlin

---

### Post by jamienos on 2007-08-05
> **merlinus said:**
> Ctrl-Alt-F1 to get to prompt (if you are not already there).

sudo dpkg-reconfigure xserver-xorg

Then:

startx

-merlin

Worked great! thanks :)

Lesson learnt: Dont edit thing's you dont have a clue about :lolflag:

---

