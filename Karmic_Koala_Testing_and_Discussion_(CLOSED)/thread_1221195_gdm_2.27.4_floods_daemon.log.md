---
title: "gdm 2.27.4 floods daemon.log"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wayne_cat on 2009-07-23
can you confirm this?

```
rschmitt@macbook:~$ sudo grep gdm /var/log/daemon.log|wc -l
1415

```logout ... login again

```
rschmitt@macbook:~$ sudo grep gdm /var/log/daemon.log|wc -l
1669
```254 new messages in the log file in a view seconds ... too much for my system monitoring.

---

### Post by MacUntu on 2009-07-23
Yes, debug mode seems enabled.

---

### Post by wayne_cat on 2009-07-23
> **MacUntu said:**
> Yes, debug mode seems enabled.

Thank you!

have not found a gdm option to remove the "-vvvvvvvvvvv" setting.

[https://bugs.launchpad.net/bugs/403723](https://bugs.launchpad.net/bugs/403723)

---

