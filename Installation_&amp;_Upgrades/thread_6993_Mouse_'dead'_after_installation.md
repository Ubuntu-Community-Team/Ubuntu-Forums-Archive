---
title: "Mouse 'dead' after installation"
date: 2004-12-03
forum: Installation &amp; Upgrades
---

### Post by Cattus Thraex on 2004-12-03
Installation (both ppc and intel) is simple, works fine, just that on my humble intel clone pc, mouse is not identified, and cannot find any solution to make it live. This also happens with suse9.x, but there is the possibility for manual setting during installation. Q: how can I make mouse live after or during installation? port is tty0?
I usually have problems connected to monitor identification, not the mouse. Help would be most useful.

---

### Post by mr_ed on 2004-12-03
It's a serial mouse, I take it?

Can you open a terminal somehow?

First thing I would try is this:
sudo ln -s /dev/ttyS0 /dev/mouse

I'm not at my Ubuntu PC atm; can someone clarify if it's /dev/mouse or if it's /dev/psaux?

---

### Post by Sorin Paliga on 2004-12-04
Thanks for the suggestion. Yes, I can play with the keyboard via Alt-F1, then tab and arrows. 
I shall try this later today (not there now). The mouse is serial, of course. The port is com1, identified by Mandrake 10.1 as tty0. Curious that the live version works fine, including mouse identification.

Anyway, a good solution would be to manually make such settings if automatic detection does not work (works fine with some distros, does not work with Ubuntu Install, SuSE 9.x etc. - but SuSE has the possibility to manually make settings, which would be welcome for Ubuntu too).

---

### Post by some11 on 2007-10-30
I have the same problem on my laptop :(
The mouse just does't work once im not booting from the CD 
Laptop is a TravelMate 2200

Keyboard is fine tho...

---

