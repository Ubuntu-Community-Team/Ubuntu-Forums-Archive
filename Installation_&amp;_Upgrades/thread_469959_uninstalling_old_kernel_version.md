---
title: "uninstalling old kernel version"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by napster86 on 2007-06-10
Hi guys,

I performed an ubuntu update which installed a newer kernel version...

Kernel Version 2.6.20.16-generic
but the older one thtis 2.6.20.15-generic is also availble i want to completely remove the older one..
how could i achieve this in command line mode..
and how to ensure tht old kernel files are completely removed,..

Thnks in advance..
you guys keep rockin in ubuntu forum..
its just a heaven for tux users..

---

### Post by zvacet on 2007-06-10
```
sudo apt-get --purge remove linux-image-2.6.20-15-generic
```

Of course if you use generic.Wich kernel do you use you can find with command 

```
uname -a
```

---

### Post by napster86 on 2007-06-10
hey zvacet 

thanx ..this forum rocks becoz of memebers like you:D

---

### Post by chris_504 on 2007-06-12
> **zvacet said:**
> ```
sudo apt-get --purge remove linux-image-2.6.20-15-generic
```

Of course if you use generic.Wich kernel do you use you can find with command 

```
uname -a
```

Thankz zvacet..u helped me too & help me regain 114Mb of valuable disk space.

One Question thou..How do you do the same using Synaptic?

---

### Post by zvacet on 2007-06-12
**synaptic>search  box>linux image**  and you will see all of them.Mark for uninstall one you want.

---

