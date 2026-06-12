---
title: "qtparted help"
date: 2005-07-14
forum: Installation &amp; Upgrades
---

### Post by artsygeek on 2005-07-14
I need this file to run qtparted: libparted-1.6.so.0
I have scoured the net and can't find it.
Please help.

---

### Post by badrinarayan on 2005-07-14
For me, I had libparted1.6-12 (apt-get install it otherwise)

```
badri@codebox:~$ sudo dpkg -S libparted-1.6
libparted1.6-12: /lib/libparted-1.6.so.12.0.8
libparted1.6-12: /lib/libparted-1.6.so.12

```

You may want to link that to libparted1.6.so.0

```
ln -s /lib/libparted-1.6.so.0 /lib/libparted-1.6.so.12
```

Does that work?

Regards
Badri

---

