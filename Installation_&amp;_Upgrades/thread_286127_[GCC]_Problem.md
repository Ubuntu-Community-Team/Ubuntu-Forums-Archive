---
title: "[GCC] Problem"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Salvatore Di Fazio on 2006-10-27
Hi guys,
I did read some posts about this problem but I couldn't resolve my problem.
If I try to use gcc to make something the system alert me that gcc isn't installed.
but if I check:

```

sudo dpkg -l | grep gcc
ii  gcc-3.3-base
ii  gcc-4.0-base
ii  libgcc1

```

Somebody told me to install the package build-essential
But I couldn't find it:

```

salvo@linux:~/Desktop$ sudo apt-cache search build | grep essential
salvo@linux:~/Desktop$

```

tnx

---

