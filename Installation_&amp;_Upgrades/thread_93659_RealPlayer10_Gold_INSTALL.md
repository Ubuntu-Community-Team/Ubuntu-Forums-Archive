---
title: "RealPlayer10 Gold INSTALL"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by Quagskag on 2005-11-22
Keep getting error messages and no such file messages:(

---

### Post by jeffjanzen on 2005-11-22
have you tried both RealPlayer10GOLD.bin and RealPlayer10GOLD.rpm?  (i prefer the rpm, so i can open it with archive manager and unpack it anywhere i want to and it works.)  if you download the bin, you're dependent on an automatic install process that is buggy, in my experience.
try the rpm.  you can either open it with archive manager or install from the terminal:
```
sudo alien -i RealPlayer10GOLD.rpm
```

---

### Post by taurus on 2005-11-22
[QUOTE=Quagskag]Keep getting error messages and no such file messages:([/QUOTE]
Isn't your error message about missing libstdc++.so.5.0???

---

