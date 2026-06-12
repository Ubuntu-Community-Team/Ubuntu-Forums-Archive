---
title: "X Server will  not load"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by metalmtb on 2006-11-11
I've burnt the iso to disk and when I try to install it comes with an error along the lines of "can't start x server, needs to be configured".  I think it may not have a driver for my video card but it's just a guess.  Any help would be apperciated!  Thanks.

---

### Post by ner0tic on 2006-11-11
does this occur while the installer gui loads?

if so download and burn the alternative install cd and do a text install.

---

### Post by metalmtb on 2006-11-11
yes it occurs when the installer gui loads.  I'll try the alternative cd and post back with the results.

---

### Post by ner0tic on 2006-11-11
after you (ingers crossed) get it installed you may need to run 
> sudo dpkg-reconfigure xserver-xorg

---

