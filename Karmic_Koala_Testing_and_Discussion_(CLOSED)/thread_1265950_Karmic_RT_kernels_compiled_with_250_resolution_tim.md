---
title: "Karmic RT kernels compiled with 250 resolution timer"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hanzomon4 on 2009-09-14
It's suppose to be 1000 for the rt-kernel. I noticed this after I installed rosegarden and it complained about a low resolution timer.

```
/boot/config-2.6.31-3-rt:CONFIG_HZ_250=y
/boot/config-2.6.31-3-rt:# CONFIG_HZ_300 is not set
/boot/config-2.6.31-4-rt:CONFIG_HZ=250
/boot/config-2.6.31-4-rt:# CONFIG_HZ_100 is not set
/boot/config-2.6.31-4-rt:# CONFIG_HZ_1000 is not set
/boot/config-2.6.31-4-rt:CONFIG_HZ_250=y
/boot/config-2.6.31-4-rt:# CONFIG_HZ_300 is not set

```

---

