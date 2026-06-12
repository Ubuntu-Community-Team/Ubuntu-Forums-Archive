---
title: "Upgraded my video card now xorg wont work"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Cows on 2007-03-03
Hey everyone, today i upgraded my ATI Radeon 9200 PRO Video card to a nVidia GeForce 7600 GS card. When I start up the ubuntu it gives me a xorg error like when I tried to install beryl and it messed up my x.server. Anyways I know its running ATI Drivers instead of nVidia and I was wondering how do I fix this without reinstalling ubuntu.

---

### Post by taurus on 2007-03-03
Get to a console with <Ctrl><Alt>F2.  Log in and run

```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by Cows on 2007-03-03
alright thanks ill post feedback =]

EDIT: Alright I got it to work thanks =].

---

