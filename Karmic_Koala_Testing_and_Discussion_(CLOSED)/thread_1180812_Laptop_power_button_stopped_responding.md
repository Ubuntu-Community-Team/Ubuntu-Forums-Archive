---
title: "Laptop power button stopped responding"
date: 2009-06-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-06-07
Dell Precision M90.

Did some updates today (the first for several days), and the hardware power button no longer responds.

---

### Post by inportb on 2009-06-07
So... you can't turn your computer on or what?

---

### Post by adult swim on 2009-06-07
i have the same problem
dell inpspiron 9400

---

### Post by yoasif on 2009-06-08
what package should this be reported to?

gnome-power-manager? it's affecting me too. :)

---

### Post by phenest on 2009-06-08
No-one seems to have reported anything, but I think gnome-power-manager is the right package.

---

### Post by MacUntu on 2009-06-08
Here too. And no, it's not about turning the machine on but about showing the shutdown menu (at least for me).

---

### Post by yoasif on 2009-06-08
Someone reported the bug, and i've added to it. 

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/384890](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/384890)

If you want to add to it, do:

apport-collect 384890

---

