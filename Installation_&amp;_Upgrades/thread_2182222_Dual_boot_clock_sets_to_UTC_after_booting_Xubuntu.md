---
title: "Dual boot clock sets to UTC after booting Xubuntu"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by broadcast23 on 2013-10-20
Here's the situation.  Upgraded Xubuntu 13.04 to 13.10, now my clock resets to UTC time when I boot into Xubuntu.  When I boot into Windows 7 I have to reset the clock to my local time which is pacific time (UTC -8). anybody know how I can stop this from happening?

---

### Post by QIII on 2013-10-20
Hello!

This one is an oldie but goodie.

Edit /etc/default/rcS

Find the line 

```
UTC=yes
```

and change it to

```
UTC=no
```

---

### Post by broadcast23 on 2013-10-20
OK Thanks I will try that now

---

### Post by ratadi2 on 2014-04-21
The setting in rcS is UTC=no
still the clock on every restart sets itself back to GMT time.
My local time is Kolkotta (India) which is what is entered in "location"
Pl help

---

