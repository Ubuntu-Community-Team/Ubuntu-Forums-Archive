---
title: "b44 ethernet driver not loading in 2.6.31-10"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-09-15
```
eric@kingfisher:~$ sudo modprobe b44
FATAL: Error inserting b44 (/lib/modules/2.6.31-10-generic/kernel/drivers/net/b44.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

dmesg log attached

---

### Post by shanix on 2009-09-15
what card are you using? Why do you need to load b44 driver? Have you check in the hardware drivers and see if you need to isntall any restricted driver??

---

