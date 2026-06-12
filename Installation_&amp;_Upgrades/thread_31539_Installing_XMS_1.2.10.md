---
title: "Installing XMS 1.2.10"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by master of all on 2005-05-03
I've got a .tar.gz of XMMS and I've done the ./configure command, but whenever i try make or make install (Or so my friend tells me) It doesn't work. Each time I get this error message
```
make: *** No targets specified and no makefile found.  Stop.
```

What am I doing (or not doing) wrong? 

(Note: I have never installed a program on ubuntu. Ever.)

---

### Post by Professor X on 2005-05-03
You don't need to compile xmms.  Read [the ubuntu guide](http://www.ubuntuguide.org) to learn how to install xmms as well as a lot of other useful apps.

---

### Post by master of all on 2005-05-04
Ok, I've installed XMMS, now how do you open/run it because I don't know how.

---

### Post by rpgcyco on 2005-05-04
Hey,

If it's not in the **Applications -> Sound & Video** menu then you can either type **killall gnome-panel** in the Terminal to reload the menus or logout and then login again.

- Rpg Cyco

---

### Post by master of all on 2005-05-04
Done the Killall gnome-panel and it's not there anywhere.

---

### Post by rpgcyco on 2005-05-05
[QUOTE=master of all]Done the Killall gnome-panel and it's not there anywhere.[/QUOTE]

Hhhmm, it seems a bit unclear whether you did actually get the original compilation method working or you installed it using apt-get (sudo apt-get install xmms).

Never the less, a way to test if it is installed is to open up the terminal and type **xmms** and press enter. If you get a 'command not found' error message, then it isn't installed correctly or at all. If that's the case, run the above command: **sudo apt-get install xmms** to install it.

It can be a bit confusing, I know, but stick with it. ;)

- Rpg Cyco

---

