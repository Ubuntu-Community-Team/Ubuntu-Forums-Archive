---
title: "fresh feisty and envy install"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by myname on 2007-06-03
I've been using envy for nvidia cards, and tried it on a fresh installation of Kubuntu feisty with an ATI card.
 
 After having envy install the ATI drivers (non manual way), the output of fglrxinfo gives me the following:
 
 ~$ fglrxinfo |grep direct
 Xlib: extension "XFree86-DRI" missing on display ":0.0".
 OpenGL renderer string: Mesa GLX Indirect

It seems that envy did not install the latest ATI drivers.

I since uninstalled the ATI drivers via Envy, and installed them the manual/long process way, and I know get this:

> 
kevinp@dugr:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6473 (8.37.6)




any ideas envy didn't work?

-Kevin

---

