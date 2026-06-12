---
title: "upgrade to 7.10 crashed now no x"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by pjhumph on 2007-12-07
Dist upgrade complained of problems with x and sent bug reports, then crashed.
Now I have no x even if in debug mode typing startx, result nothing.
Can I recover this, I've downloaded iso image to a cd. Can I reinstall and recover my settings etc in /home.
 Philip

---

### Post by Ub1476 on 2007-12-07
When you boot the live cd you can access the other partitions on your comp, so no problem there. You can try to reconfigure X first though:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by pjhumph on 2007-12-07
Result. Thank you sorted. Was able to recofigure xserver.

---

