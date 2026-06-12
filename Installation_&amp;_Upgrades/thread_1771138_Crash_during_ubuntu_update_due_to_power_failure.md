---
title: "Crash during ubuntu update due to power failure"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by drakejacob on 2011-05-30
I was updating my system when the power to my system was cut off. So how do I get to know whether the updates were installed correctly or not?

---

### Post by zvacet on 2011-05-30
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by drakejacob on 2011-05-30
> **zvacet said:**
> ```
sudo dpkg --configure -a
sudo apt-get -f install
```

Thank you for the help.My problem is solved.

---

