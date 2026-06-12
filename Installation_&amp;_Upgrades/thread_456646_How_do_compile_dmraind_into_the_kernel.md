---
title: "How do compile dmraind into the kernel?"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by burzum on 2007-05-27
I've did this:

```
aptitude install linux-source-2.6.15
tar xvjf linux-source-2.6.15.tar.bz2
cd linux-source-2.6.15
cp /boot/config-2.6.15-26-server .config
nano .config
```

But i can't find anything dmraid related in the .config file and i don't have any idea how to include it into the kernel. Can anyone help me please?

---

### Post by Medieval_Creations on 2007-05-27
I'm assuming your trying to create the dmraid module to create a raid?

Why not just use mdadm.  It's in the repositories so you can just apt-get it.

---

