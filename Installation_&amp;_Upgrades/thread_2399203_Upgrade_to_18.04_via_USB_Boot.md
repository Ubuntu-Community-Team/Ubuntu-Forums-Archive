---
title: "Upgrade to 18.04 via USB Boot"
date: 2018-08-22
forum: Installation &amp; Upgrades
---

### Post by geoff20 on 2018-08-22
Have a working 18.04 on USB and a 16.04 on a NUC.
If I install 18.04 will I lose my 16.04 settings.
Do not want to upgrade directly from 16.04 as I encountered internet connections when I tried it before.

---

### Post by C.S.Cameron on 2018-08-23
You can copy home directory to a safe place using **rsync**, (or the GUI **grsync**).
After upgrade to 18.04, you can replace the new home with the copy.
[https://sourceforge.net/projects/grsync/](https://sourceforge.net/projects/grsync/)

You will need to reinstall any user installed programs you want to keep.

---

