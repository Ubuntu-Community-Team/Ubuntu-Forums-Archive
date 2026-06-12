---
title: "VNC, X11, qt, VirtualBox not handling keyboard together on 18.4.2"
date: 2019-06-14
forum: Installation &amp; Upgrades
---

### Post by rick-scw on 2019-06-14
I have an Ubuntu 18.4.2 updated base image running in a cloud, with the intention of using it to create nested VMs using VirtualBox, using VNC to access the desktop VirtualBox application. (Standard OpenStack setup)

I installed Virtualbox (apt install) which seemed to go ok. But, when I start virtualBox from a terminal within a VNC session, I get a warning from Qt.  "Qt: XKEYBOARD extension not present on the X server".  Sure enough, when I try to type characters into the VirtualBox app, the keyboard events are not mapping correctly (e.g. asdf becomes abfh).

I've tried adding XKB_DEFAULT_RULES=base  and QT_XKB_CONFIG_ROOT=/user/share/X11/xkb to my xstartup file in the .vnc folder.  That did not help.  

localectl shows the X11 layout to be pc104 right now, but I've tried a few different values. Changing this does not seem to have any effect.

The root issue seems to be that Qt is expecting to find keyboard information from the X server (Gnome in my case) but fails.  In this situation, there is no local keyboard. I'm not sure how my remote keyboard profile is supposed to find its way from my VNC client into the X11 environment, so Qt can read it. I haven't had any luck finding that answer through google.

Any suggestions on a path forward?

---

