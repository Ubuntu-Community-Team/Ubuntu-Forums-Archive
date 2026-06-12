---
title: "From Breezy to Dapper"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by pmatos on 2008-03-20
Hello all,

A breezy CD was all I had handy to get a machine up and running fast.
Once I had breezy up and running I thought about updating to dapper, given that it would be nice to have a more recent version. After the upgrade, the X server failed because the module mouse can't be found. 

What I found out was that during upgrade, new module xserver-xorg-input-mouse was installed into /usr/lib/xorg while current xserver is looking for modules into /usr/X11R6. So, now I have two changes, either upgrade all of X or downgrade the module. I can't get any option to work.

The upgrade fails because it says some packages can't be found. The downgrade fails because it says it can't find the previous mouse driver vesion 6.8.2-77.

Any ideas?

Cheers,

Paulo Matos

---

### Post by zvacet on 2008-03-21
```
sudo dpkg-reconfigure xserver-xorg
```

---

