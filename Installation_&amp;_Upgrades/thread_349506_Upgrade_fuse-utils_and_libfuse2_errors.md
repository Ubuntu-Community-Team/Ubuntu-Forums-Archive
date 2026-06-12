---
title: "Upgrade fuse-utils and libfuse2 errors"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by Copperteeth on 2007-01-30
As the thread topic states im having trouble installing the newest versions of fuse-utils and libfuse. The software Update manager wants me to upgrade those 2 programs but when i go to upgrade im returned with the following error:
```
E: /var/cache/apt/archives/fuse-utils_2.6.1-0givre4_i386.deb: subprocess new pre-removal script returned error exit status 1
E: /var/cache/apt/archives/libfuse2_2.6.1-0givre4_i386.deb: conflicting packages - not installing libfuse2

```

how do i fix it and what should i do?

---

### Post by taurus on 2007-01-30
What happens if you run these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo aptitude clean
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by Copperteeth on 2007-01-30
alright, that solved it, imma write those commands down for next time.
thanks a lot

---

### Post by taurus on 2007-01-30
You're welcome.

---

