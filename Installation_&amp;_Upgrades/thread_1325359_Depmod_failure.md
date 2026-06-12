---
title: "Depmod failure"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by squibsy on 2009-11-13
Every time I run the update manager, depmod fails:

E: linux-image-2.6.28-16-generic: subprocess installed post-installation script returned error exit status 1
E: linux-restricted-modules-2.6.28-16-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured

How can I go about debugging this? I'm running Karmic.

Thanks for reading.

---

### Post by squibsy on 2009-11-15
bumpity

---

### Post by squibsy on 2009-11-15
Final bump - reluctantly returning to XP tomorrow.

---

### Post by efflandt on 2009-11-15
Are you by any chance running kernel 2.6.28-16 instead of the Karmic kernel 2.6.31-14?  There have been changes that may not work with the older kernel (like sound).

---

### Post by squibsy on 2009-11-16
I don't appear to be:
```
cat /proc/version
Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009
```

---

