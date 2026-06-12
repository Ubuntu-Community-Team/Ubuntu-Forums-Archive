---
title: "GEM memory leak from GLX 1.4 backport, first step"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2010-05-15
Hi there:

I can confirm my machine's GLX version is 1.4, and I definitively get the slow down problem, however, after running in a terminal:

```
grep "object bytes" /sys/kernel/debug/dri/0/gem_objects
grep: /sys/kernel/debug/dri/0/gem_objects: No such file or directory
```

What am I doing wrong?

cheers

---

### Post by hihihi100 on 2010-05-16
NVidia drivers dont use GEM, my memory leak is a different bug

---

