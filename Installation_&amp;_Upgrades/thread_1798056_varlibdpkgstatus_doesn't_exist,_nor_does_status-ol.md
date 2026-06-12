---
title: "/var/lib/dpkg/status doesn't exist, nor does status-old, nor does status.broke"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by benjabean1 on 2011-07-05
I try running sudo apt-get update:
```
Reading package lists... Error!
E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.
```
So I try running sudo dpkg --configure -a, and I get the same thing.

Here's the output of ls /var/lib/dpkg:
```
lock
```

I've tried searching for other posts like mine, but most of the other problems have been resolved by copying status-old or status-broke into status.

---

