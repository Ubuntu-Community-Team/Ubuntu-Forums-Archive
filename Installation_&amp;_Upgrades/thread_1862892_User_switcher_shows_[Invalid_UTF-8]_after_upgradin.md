---
title: "User switcher shows [Invalid UTF-8] after upgrading"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by sundman on 2011-10-17
After upgrading to 10.11 the user switcher showed 
```
[Invalid UTF-8]
```.

It can be fixed by adjusting MIN_UID ```
/etc/login.defs
``` to an appropriate value. The value can be wrong if some kind of external user management is used.

See [[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/834137]](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/834137])

---

