---
title: "Touchpad suddenly stopped working on Intrepid.. how to debug?"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lapalorky on 2008-10-02
While trying to figure out some issues regarding system sounds I played around in the GNOME Sound GUI. Suddenly the mouse stopped moving. I was sure a restart of X would solve it, or at least a complete reboot. But neither worked.

In my frustration I tried apt-get install --reinstall xserver-xorg but without solving the problem. I even edited the /etc/X11/xorg.conf and added some information about my mouse (Synaptics TouchPad) and strangely there wasn't anything in that file about any mouse.

If you need any output from the mentioned machine you guys first have to tell me how to navigate GNOME without a mouse, to be able to Copy & Paste information here. Right now I'm sitting on a different machine.

Appreciate any thoughts!

---

### Post by nbubis on 2008-10-12
Asumming this is indeed a software problem (it sounds odd that the mouse stopped working suddenly), this sounds similar to the following threads, except for the fact that in most of the other reports the mouse function works but the scrolling doesn't. 

I suggest you report the bug in one of the threads, as well as reading up on a number of possible fixes suggested in them.

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/247608]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/247608")

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/278585]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/278585")

If you want the cutting edge - you better be prepared to shed blood.

---

