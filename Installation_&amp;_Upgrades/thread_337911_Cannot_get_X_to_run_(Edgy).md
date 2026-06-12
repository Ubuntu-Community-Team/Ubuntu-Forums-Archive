---
title: "Cannot get X to run (Edgy)"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by sfpiano on 2007-01-13
I installed edgy, but when I run startx, I get this:
```
(WW) fglrx: No matching Device section for instance (BusID PCI:1:11:0) found
(EE) No devices detected
Fatal error: No screens found
XIO: fatal IO error 104 on X server ":0.0" after 0 requests
```

This is after I ran dpkg-reconfigure xserver-xorg

Then if I run fglrxinfo I get:
```
Error: unable to open display :0
```

---

