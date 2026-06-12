---
title: "Toshiba A35-s159 laptop wont install Ubuntu"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by dangd301 on 2010-05-07
Get a black screen trying to install Ubuntu in Toshiba a35-s159  laptop

---

### Post by Catharsis on 2010-05-07
I believe you have an Intel 852GM graphics card. To check, run this in a terminal:
```
lspci | grep VGA
```

If so, see:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

