---
title: "problems with x11 libraries after updates"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by rosanna.sordo on 2011-12-28
Hi,

I use a software (MOOG), which requires libX11.a.
This software was working properly on kubuntu (both 64 and on 2 different 32 bit distro). After an update, it doesn't work anymore and it is not possible to compile it again. 
The errors are pointing to X11:
-----
In function `x11_setup':
undefined reference to `XSetErrorHandler'
undefined reference to `XSetIOErrorHandler'
...
and a zillion of othere undefined references
-------

libX11.a is installed on my pcs, from libx11-dev (2:1,4,4.2ubuntu1).

Any idea on what went wrong and/or how to solve it?

thanks

Rosanna

---

