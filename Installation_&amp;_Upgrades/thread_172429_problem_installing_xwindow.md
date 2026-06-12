---
title: "problem installing xwindow"
date: 2006-05-08
forum: Installation &amp; Upgrades
---

### Post by zenkoanlife on 2006-05-08
I just installed 5.10 on an old machine using the "bare bones" server installation option. I am now trying to add fluxbox and have a problem with the x window system. when I type startx I get a few screen flashes and end up back at the terminal with the following output....

skipping "/usr/X11R6/lib/modules.libfb.a:fbmmx.o": no symbols found
Warning: font renderer for "pcf" already registered at priority 0
about a dozen more Warning: font renderer ....etc. lines

Is there something else I should be installing for the fonts, and/or some configurations I need to do? so far the only things i've installed with apt are fluxbox, xdm and x-window-system-core.

---

### Post by Sef on 2006-05-08
read this:

[http://doc.gwos.org/index.php/FluxboxSource]("http://doc.gwos.org/index.php/FluxboxSource")

and this

[https://wiki.ubuntu.com/Fluxbox]("https://wiki.ubuntu.com/Fluxbox")

---

### Post by zenkoanlife on 2006-05-09
Thanks for the links. found some good info... that wiki page was what I was using as a guide to begin with.... my problem seems to be with the X-window system, not fluxbox. :confused:

---

### Post by zenkoanlife on 2006-05-16
I'm not sure what I did, but everything is working now... well, i know what i did, i just don't know which of the 1000 things i tried worked :-) fluxbox is working anyway.

---

