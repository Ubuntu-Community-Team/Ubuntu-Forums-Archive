---
title: "[ drm:intelfb_restore ] ERROR"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by radocha on 2009-11-25
hello

I`ve a motherboard asrock p5gc-mx/1333 with i945g chipset.
Durring the instalation of ubuntu 9.10 I recive a notice:

[drm:intelfb_restore] *ERROR* Failed to restore crtc configuration - 22

I heard there is a problem with intel graphic but couldn`t find any tips how to resolve this.

Is anyone here how can help with this problem?

---

### Post by yc2rdw on 2009-12-02
I experienced same problem too for weeks, and the way out was very silly and stupid... change my monitor !
I did it that way, changed my monitor with a new one which able to communicate with graphic card (I was using an old monitor for installation), and voilaa... it ran just fine !
Seems like Ubuntu tried to find out what kind of monitor and graphic card you have on the system, when it failed to figure it out, the error massage flood into our screen. 

Well... at least it work for me... :)

PS : Tried on Ubuntu 9.10, Ubuntu 9.10 64bit and UbuntuStudio 9.10

---

### Post by radocha on 2010-02-08
My problem was monitor plugin into KVM, when i connected it directly to the computer the problem resolved

---

