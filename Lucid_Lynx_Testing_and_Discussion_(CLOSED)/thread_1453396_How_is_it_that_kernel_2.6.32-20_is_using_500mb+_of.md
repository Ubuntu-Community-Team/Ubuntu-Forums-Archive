---
title: "How is it that kernel 2.6.32-20 is using 500mb+ of memory?"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-13
why does this kernel is taking so much memory when 2.6.33 take only 150-200mb?

---

### Post by philinux on 2010-04-13
Worse here and only got firefox running.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2009       1304        704          0         19        504
-/+ buffers/cache:        780       1228
Swap:         1906          0       1906

```

---

### Post by jfernyhough on 2010-04-13
Might this be down to ureadahead doing some preloading/caching?

---

### Post by aviramof on 2010-04-13
is it good or bad?

```
free -m
             total       used       free     shared    buffers      cached
Mem:          2012       1934         77          0         19        1549
-/+ buffers/cache:        365       1647
Swap:         1952          0       1952
```

it's after restart now but not long ago it was 500MB+ for no apparent reason.

---

### Post by philinux on 2010-04-13
Just did a restart. At desktop nothing else running. 333meg is defo good.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2009        592       1416          0         55        203
-/+ buffers/cache:        **[COLOR="Red"]333[/COLOR]**       1676
Swap:         1906          0       1906

```

It's only gone up to 400meg with FF running so it must have just been a glitch.

I'll keep an eye on it.

Ah this bug. [https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

---

### Post by Longinus00 on 2010-04-13
This bug was introduced in karmic. You guys sure are slow catching on ;)

---

