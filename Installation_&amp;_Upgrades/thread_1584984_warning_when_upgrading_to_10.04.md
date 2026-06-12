---
title: "warning when upgrading to 10.04"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by ubun_tut on 2010-09-29
i am trying to upgrade to ubuntu 10.04 from 8.04, and am getting this warning:

"Upgrading may reduce desktop effects, and performance in games and other graphically intensive programs.

This computer is currently using the AMD 'fglrx' graphics driver. No version of this driver is available that works with your hardware in Ubuntu 10.04 LTS.

Do you want to continue?"

should i continue? i have no idea what a 'fglrx graphics driver' is. thanks.

---

### Post by Frogs Hair on 2010-09-29
Posting your hardware specs may be helpful your graphics card or chip may be outdated .

---

### Post by ubun_tut on 2010-09-29
hi, i get:

```

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

```

when i type "lspci | grep VGA" at the command.

---

### Post by Frogs Hair on 2010-09-30
> **ubun_tut said:**
> hi, i get:
 
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

```
 
when i type "lspci | grep VGA" at the command.
 
I have done some searching and have not found a Linux driver for a ATI X300 yet . I find Windows drivers and they are under the outdated catigory .

---

### Post by ubun_tut on 2010-09-30
i see. maybe my computer is too old :p

i guess i shouldn't be upgrading in that case.

---

