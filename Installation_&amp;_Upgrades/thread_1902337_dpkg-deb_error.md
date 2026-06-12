---
title: "dpkg-deb error"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by kinguzzo on 2011-12-30
Hi,
i'm just trying to install some dependencies for an openflow controller on a virtual machine created with Netkit. At one point i have this error
```

Errors were encountered while processing:
/var/cache/apt/archives/sensible-utils_0.0.6_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
 and the installation fail. 

and when i try to start the boot file that i need i have this error

```

./boot.sh: line 97: autoreconf: command not found

```

Is the first issues bound to the second?
how can i solve this problem?
pls help me
regards
F.P.

---

### Post by zvacet on 2012-01-04
Try with 

```
sudo dpkg --configure -a
```

---

