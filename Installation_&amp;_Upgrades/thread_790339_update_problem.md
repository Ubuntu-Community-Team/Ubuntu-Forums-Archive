---
title: "update problem"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by darkblade8801 on 2008-05-11
hi everyone, i am a new user to Ubuntu. And i having some trouble with installing updates i get the error that it says (E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

E:

   so pls guys if you can help me at all it would be very grateful.

---

### Post by divague on 2008-05-11
Go to Applications->Accessories->Terminal and type:

sudo dpkg --configure -a

it'll ask for your password type it press enteer, and this should fix that problem

---

