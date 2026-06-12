---
title: "ati catalyst 8.3 for ubuntu 7.10 problem"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by toohottofix on 2008-03-14
Hi,

I can't get ati catalyst 8.3 installed. The opengl vendor string is always the "Mesa project: www.mesa3d.org" :confused:

anybody know how to fix it?

Thanks.

---

### Post by overdrank on 2008-03-15
> **toohottofix said:**
> Hi,

I can't get ati catalyst 8.3 installed. The opengl vendor string is always the "Mesa project: www.mesa3d.org" :confused:

anybody know how to fix it?

Thanks.
Hi and welcome, what is the model of the graphics card and have you looked at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by toohottofix on 2008-03-17
ATI catalyst 8.3 was successfully installed after a couple of re-installation.

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) works. THANKS! :cool:

The trick is the "DEPENDENCY". Get all dependencies installed before installing the real meat (ati catalyst 8.3)

An new "icon" will be shown on the panel bar after rebooting the system. Just click the icon and everything will be done perfectly.

Then type "fglrxinfo" to have a check. it will show the following.

display: :0.0 screen: 0
OpenGL vender string: ATI Technologies Inc.
OpenGL renderer string: ATI <your display card model>
OpenGL version string: 2.1.7412 Release

Thanks those who try to help during past couple of days.

---

### Post by Ub1476 on 2008-03-17
Here's an awesome thread for tips and tricks to add to xorg.conf if using the Catalyst 8.03 driver: [Setup an ATI card with the new FGLRX drivers for Compiz-Fusion]("http://forum.compiz-fusion.org/showthread.php?t=6794&page=1").

---

