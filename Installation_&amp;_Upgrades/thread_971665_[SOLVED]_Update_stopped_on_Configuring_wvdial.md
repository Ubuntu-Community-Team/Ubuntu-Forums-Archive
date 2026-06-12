---
title: "[SOLVED] Update stopped on Configuring wvdial"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by kaspar_silas on 2008-11-05
Hi All,

My 8.10 upgrade is stuck on Configuring wvdial


The details it gave 

```
Setting up vino (2.24.1-0ubuntu1) ...

Setting up wvdial (1.60.1+nmu2) ...
```



It's not froze but nothing has changed in over 30 minutes and it was flying through line after line before. 

I can still use the system and terminal so does anyone know anything I can do to skip this and come back later.

All help greatly appreciated.

---

### Post by kaspar_silas on 2008-11-05
Just a little update:

I got brave and pressed crtl+c to skipped the wvdial step. The upgrade popped up some moaning messages about it being incomplete but it pressed on. It completed without restarting but with a final error message.

I removed wvdial and reran it. After the restart (and reinstalling the nvidia driver all went splendidly).

Hurra!

---

