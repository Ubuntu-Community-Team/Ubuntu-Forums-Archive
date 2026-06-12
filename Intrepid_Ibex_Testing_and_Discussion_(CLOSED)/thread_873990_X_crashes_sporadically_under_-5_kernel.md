---
title: "X crashes sporadically under -5 kernel"
date: 2008-07-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by klange on 2008-07-29
First crash was before gdm even started, second happened shortly after logging in. Reverted to -4 and all is well.

Intel (945) graphics, fairly standard set up.

Log says the following:
```
Xorg[7553]: segfault at 61486771 ip b7a587cc sp bfd4e5e0 error 4 in wacom_drv.so[b7a55000+13000]
```

Nothing in there for the second crash.

---

