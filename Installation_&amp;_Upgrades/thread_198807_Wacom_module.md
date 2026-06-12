---
title: "Wacom module?"
date: 2006-06-17
forum: Installation &amp; Upgrades
---

### Post by freeridr on 2006-06-17
problem: no graphical interface

error: no devices detected / no screens found or monitor goes blank.

solved: use the "vesa" driver, but the "vesa" driver wasn't showing up as an option.

```
apt-get install xserver-xorg-driver-vesa
```

this solution has been posted elsewhere but i can't delete it so hopefully it will help someone. cheers!

---

