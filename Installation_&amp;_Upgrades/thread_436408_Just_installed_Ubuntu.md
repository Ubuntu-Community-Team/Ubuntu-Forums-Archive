---
title: "Just installed Ubuntu"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by dojbo on 2007-05-07
I just installed Ubuntu on an extra hard drive (running windows right now on C).  And when I go to boot from the D drive, I get an error reading the nVidia Graphics driver.  It seems like Ubuntu is loaded, but there is no GUI only a dos-like program.  Anyone know what is going on?

---

### Post by zvacet on 2007-05-08
ctrl+alt+F1

```
 sudo dpkg-reconfigure xserver-xorg
```


replace **nvidia** with **nv** and after that you can go and find proper drivers for your card

---

