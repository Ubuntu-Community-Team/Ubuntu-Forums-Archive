---
title: "missed termcap library"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by Scarios on 2007-09-19
Hi,

I use Ubuntu 6.10 on my labtop (HP intel  Pentium dual core).
I was triying to install a software . But when i made
*make all*
 an error message appear at the end of compilation process

[B]usr/bin/ld: cannot find -ltermcap
collect2: ld returned 1 exit status
make: *** [gsac] Error [/B]1

Where i can find the termcap library and how to install.
thanks
scarios

---

### Post by kingdogbert on 2007-10-22
I ran into a similiar problem and found a solution here:
[http://ubuntuforums.org/showthread.php?t=476228](http://ubuntuforums.org/showthread.php?t=476228)

Basically, replace -ltermcap with -lncurses and install libncurses5-dev with Synaptic. Goodluck

---

