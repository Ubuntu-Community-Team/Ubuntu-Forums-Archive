---
title: "Ubuntu 16.04 libopenmpi-dev symbolic link errors."
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2016-04-22
It looks there are some errors about libopenmpi-dev symbolic links ????

```

.../usr/lib$ sudo ln -sf libmca_common_sm.so.4 libmca_common_sm.so
...:/usr/lib$ sudo ln -sf libopen-pal.so.13 libopen-pal.so
...:/usr/lib$ sudo ln -sf libopen-rte.so.12 libopen-rte.so

```

And, I still have "liboshmem.so" missing, it's
```

:/usr/lib$ ls -ls liboshmem.so 
0 lrwxrwxrwx 1 root root 18 Feb 25 08:43 liboshmem.so -> liboshmem.so.8.1.0

```
but **liboshmem.so.8.1.0** is also missing ...


Any suggestions?


Cheers
Pei

---

