---
title: "fsck failed super block write time in future."
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jithin1987 on 2009-09-02
My system is freezing after resuming from sleep. So only way after is sysreq RSEIUB. And the next immediate boot fails.

It says fsck failed because of unexpected inconsistency. My super block write time in future and so I have to run fsck manually. In jaunty there was no such issue when using RSEIUB.

---

### Post by taavikko on 2009-09-02
[http://ubuntuforums.org/showthread.php?t=1252108](http://ubuntuforums.org/showthread.php?t=1252108)

---

### Post by kansasnoob on 2009-09-02
> **jithin1987 said:**
> My system is freezing after resuming from sleep. So only way after is sysreq RSEIUB. And the next immediate boot fails.

It says fsck failed because of unexpected inconsistency. My super block write time in future and so I have to run fsck manually. In jaunty there was no such issue when using RSEIUB.

I don't use hibernate or sleep but I had that with kernel version -8, after updating to the -9 kernel alls well.

---

### Post by philinux on 2009-09-02
Hibernate works ok on this hardware.

---

