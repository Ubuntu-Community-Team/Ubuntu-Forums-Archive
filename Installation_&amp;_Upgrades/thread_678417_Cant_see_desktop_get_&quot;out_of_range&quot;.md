---
title: "Cant see desktop get &quot;out of range&quot;"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by mla_ca520 on 2008-01-25
I installed the ati drivers and now every time I try to boot, I get a screen stating "out of range" and that I have to set my screen to 1680x1050 with 60 mhz.  How do I change these settings now...especially since I can't see the OS any more.

---

### Post by PmDematagoda on 2008-01-25
Boot Ubuntu in Recovery Mode, then execute:-
```
sudo dpkg-reconfigure xserver-xorg
```
Then select the proper resolution and refresh rate.

---

