---
title: "Can't find the file that invokes xsplash at boot"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Locke_99GS on 2009-09-29
Where exactly on the system is xsplash invoked at boottime??

---

### Post by tad1073 on 2009-09-29
open a terminal and type:
```
find xsplash
```

---

### Post by Locke_99GS on 2009-09-29
I know where it exists on the system, I want to know what process invokes it and how. I can't find it in any rc*.d scripts or init(.d)

---

### Post by MacUntu on 2009-09-29
/etc/gdm/Init/Default and /etc/gdm/PreSession/Default

---

### Post by Locke_99GS on 2009-09-29
That is exactly what I was looking for. Thank you, MacUntu.

---

