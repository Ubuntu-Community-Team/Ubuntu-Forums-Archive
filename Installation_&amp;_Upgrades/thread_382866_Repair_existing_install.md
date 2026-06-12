---
title: "Repair existing install"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by W@LT on 2007-03-12
Hi

Installing new graphics card has screwed Ubuntu and it will now not load..

Is there a repair function?

---

### Post by zvacet on 2007-03-12
Not load or don´t have graphic?If it is just that you don´t have graphic login type
ctrl+alt+F1
You will find yourself in terminal.After that
```
 sudo dpkg-reconfigure xserver-xorg
```
and pick your new grafic card from list.

---

