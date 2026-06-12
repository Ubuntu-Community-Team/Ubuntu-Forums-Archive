---
title: "Apt - Installation Order For Multiple Packages Installed Together"
date: 2021-03-07
forum: Installation &amp; Upgrades
---

### Post by Alan5127 on 2021-03-07
Hi All,

I am wondering if the order in which I list multiple packages to install using 'apt' is important, or will 'apt' just auto-magically work it out, and install in the 'best' order (whatever that may be)?

For example, would or could it ever make a difference whether I used:

```
# apt install package1 package2
```

compared to:

```
# apt install package2 package1
```


Thanks,

Alan.

---

### Post by Impavidus on 2021-03-07
Normally the order doesn't matter. If you somehow managed to break package management and have to fix things manually while struggling with limited hard drive space, it may matter.

Some packages have pre-dependencies. In those cases, pre-dependency X of package Y isn't only needed to use Y, but also to install Y, so that X must be fully installed before installation of Y can start. This is handled automatically.

---

### Post by Alan5127 on 2021-03-07
> **Impavidus said:**
> Normally the order doesn't matter. If you somehow managed to break package management and have to fix things manually while struggling with limited hard drive space, it may matter.

Some packages have pre-dependencies. In those cases, pre-dependency X of package Y isn't only needed to use Y, but also to install Y, so that X must be fully installed before installation of Y can start. This is handled automatically.


Thanks Impavidus,

Alan.

---

