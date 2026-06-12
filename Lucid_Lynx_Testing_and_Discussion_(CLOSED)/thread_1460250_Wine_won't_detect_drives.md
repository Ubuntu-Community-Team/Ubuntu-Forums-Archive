---
title: "Wine won't detect drives"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by A_T on 2010-04-22
Running Lucid and Wine 1.1.43. Wine won't detect my drives - and using autodetect doesn't help.

---

### Post by mc4man on 2010-04-22
Lucid doesn't write fstab entry for your cd/dvd drive(s), so atm no fstab - no drive detection in wine. (unless media with a filesystem is in drive when wine is opened.

If you need a drive 'detected' for an prog then check if the the prog's options allow for an IO of ASPI-WNASPI32.DLL - this allows prog to communicate directly with hardware

Otherwise depending on what you need to do there are some workarounds - if none are  suitable then a typical fstab entry(s) and mountpoint(s) can be created

---

### Post by A_T on 2010-04-23
So will this be fixed in Lucid final?

---

### Post by dino99 on 2010-04-23
> **A_T said:**
> So will this be fixed in Lucid final?

wine is not lucid  :lolflag:

go to apps wine winecfg : what have you into drives tab ? opt_in show hidden files on the botom tab

---

### Post by A_T on 2010-04-23
Where did I say Wine was Lucid?

Anyway using the aspi layer enables ImgBurn to see the DVD drive so thanks to mc4man.

---

