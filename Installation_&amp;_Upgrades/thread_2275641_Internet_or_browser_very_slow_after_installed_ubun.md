---
title: "Internet or browser very slow after installed ubuntu 15"
date: 2015-04-27
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2015-04-27
I really have the problem of finding out what my problem is.
I have installed ubuntu 15 on laptop 
but it has slow my browsing, the sites run longer before to load,I have a fast connection 
so I don't really know where the problem can be.

---

### Post by Vladlenin5000 on 2015-04-27
> **hoboy said:**
> I don't really know where the problem can be.

Nobody knows. Perhaps if you post relevant info about the system's specs, Ubuntu version, etc. someone might have an idea. Otherwise it's a complete waste of time.

---

### Post by MikeMecanic on 2015-04-28
Did you try Google Chrome?  Are you running it alone?  Whar type of installation did you do?
  Running it alone, I choose the LVM option during installation and it's quite and stable.  Everything seem to be faster. What did you do during post installation and did you removed an Ubuntu component after installation?  Does your swap partition is saturated?  Did you try to clear the cache?

```
sync; echo 3 | sudo tee /proc/sys/vm/drop_caches
```
Check the swap partition
```
free
sudo swapoff -a
free
sudo swapon -a
free
```

Regards,

---

