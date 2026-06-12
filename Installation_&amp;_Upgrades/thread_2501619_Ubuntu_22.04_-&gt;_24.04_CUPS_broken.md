---
title: "Ubuntu 22.04 -&gt; 24.04 CUPS broken"
date: 2024-10-15
forum: Installation &amp; Upgrades
---

### Post by john163 on 2024-10-15
I can no longer print after upgrading.  Searching led me to something interesting:

```

joliver@blinky:/tmp/canon/linux-UFRII-drv-v600-us$ apt list | grep cups | grep residual

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

cndrvcups-common/now 4.00-1 amd64 [residual-config]
cndrvcups-ufr2-us/now 3.60-1 amd64 [residual-config]
joliver@blinky:/tmp/canon/linux-UFRII-drv-v600-us$ sudo apt-get install cndrvcups-common cndrvcups-ufr2-us
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package cndrvcups-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  cndrvcups-ufr2-us

Package cndrvcups-ufr2-us is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  cndrvcups-common

E: Package 'cndrvcups-common' has no installation candidate
E: Package 'cndrvcups-ufr2-us' has no installation candidate

```

Sooooo... how do I print now???

---

### Post by john163 on 2024-10-15
So, it turns out those were old Canon drivers.  I manually removed them with dpkg -P  

In case anyone finds this issue while looking for help... the Canon install script insists on trying to install libcupsys2, which apparently doesn't exist.  So I told it to install anyway.  At the end, it claimed the install had failed, but I can print, so... problem solved!

---

