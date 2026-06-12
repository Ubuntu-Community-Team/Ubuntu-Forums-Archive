---
title: "[SOLVED] cant fix HDD error for install"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by Lateforgym on 2008-09-03
I have run error check in windows about 6 times and gparted keeps sayign my primary has an error from a bad sector. What gives?

---

### Post by Titan8990 on 2008-09-03
HDD could be bad...

---

### Post by Lateforgym on 2008-09-03
yea but if the hdd is bad why does windows say its ok but gparted say no?

---

### Post by Lateforgym on 2008-09-03
Ill answer my own question for the archives, since this took hours of searching and playing around. Windows HDD (hard disk drive) Error Checker (chkdsk /f /r) is not as in-depth as gparted's (ubuntu's built-in Partition Editor) error checking. Also HDD manufacturers tools are also more in-depth. I confirmed this with Seagate's DOS HDD tools. Dont waste your time with the Windows version of Seagate's tools, it is buggy and the "generic" tests are also not as in-depth.  The DOS version also allows you to your Seagate drive, where as the Windows version just saying "failed" and giving you no other info.

---

