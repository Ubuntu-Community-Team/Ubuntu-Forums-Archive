---
title: "Looks like I've got a memory leak."
date: 2009-12-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-12-02
It's showing 700 meg used.

Only extra stuff running is ubuntu one and firefox. Normally I would be at around 400 meg.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2009       1475        533          0         56        710
-/+ buffers/cache:        708       1300
Swap:         1906          0       1906

```

---

### Post by Grenage on 2009-12-02
Does top reveal any more info on what processes might be using it?

---

### Post by philinux on 2009-12-02
Not really I had looked at that first.

---

### Post by gradinaruvasile on 2009-12-02
Launch top, then press shift+o then q. you will have the apps ordered by memory usage (res).

---

### Post by philinux on 2009-12-02
> **gradinaruvasile said:**
> Launch top, then press shift+o then q. you will have the apps ordered by memory usage (res).

Ok.

---

### Post by gradinaruvasile on 2009-12-02
I dont see anything suspicious there. Probably that memory will be freed when needed.

---

### Post by philinux on 2009-12-02
> **gradinaruvasile said:**
> I dont see anything suspicious there. Probably that memory will be freed when needed.

Gone up now at 762. I suspect ubuntu one.

philinux@philinux-testing:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2009       1951         57          0         67       1121
-/+ buffers/cache:        762       1246
Swap:         1906          0       1906


I will reboot after its finished syncing.

---

### Post by philinux on 2009-12-02
Rebooted and now I've got the more usual 440 meg used.

64 bit by the way.

I'll give a few mins to settle down and then connect up ubuntu one and see if it's the culprit.

---

