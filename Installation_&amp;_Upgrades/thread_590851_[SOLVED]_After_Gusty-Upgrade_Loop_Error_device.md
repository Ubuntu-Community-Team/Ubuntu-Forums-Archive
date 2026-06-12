---
title: "[SOLVED] After Gusty-Upgrade: Loop Error device"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Archmage on 2007-10-25
After upgrading to gusty, I'm getting some strange error-messages about a failure in the loop device over my console, when I try to load the new kernel. Also the home-partion seems not to be loaded. (It is a normal ext3-partition.)

What can I do? I did try for updates but there are no new ones there.

---

### Post by Archmage on 2007-10-29
In case someone finds this via searching:

You need to remove the evms-package to make your system useable. E.g.

```

sudo aptitude remove evms

```

---

