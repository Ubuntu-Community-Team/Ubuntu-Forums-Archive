---
title: "cant install the new update today"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by sirab on 2007-05-26
when i click install i get this error message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i run the dpkg i get this error

sirab@sirab-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
sirab@sirab-laptop:~$ 

what do i do?

---

### Post by sirab on 2007-05-26
figured it out dont worryt about it

---

### Post by earobinson on 2007-05-26
I assime the problem was that you where missing a sudo infront of > dpkg --configure -a so when you did > sudo dpkg --configure -a everyhing worked?

---

