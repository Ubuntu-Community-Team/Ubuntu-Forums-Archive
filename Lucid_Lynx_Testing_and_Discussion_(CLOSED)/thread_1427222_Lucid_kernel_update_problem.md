---
title: "Lucid kernel update problem"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by henwyn on 2010-03-11
The last three kernel updates under Lucid have installed but configuration has stalled each time. I thought waiting might sort this out but I guess not. Here is the error message synaptic gives:

E: linux-image-2.6.32-14-generic: subprocess installed post-installation script returned error exit status 2
E: linux-backports-modules-nouveau-2.6.32-14-generic: dependency problems - leaving unconfigured
E: linux-image-2.6.32-15-generic: subprocess installed post-installation script returned error exit status 2
E: linux-backports-modules-nouveau-2.6.32-15-generic: dependency problems - leaving unconfigured
E: linux-image-2.6.32-16-generic: subprocess installed post-installation script returned error exit status 2
E: linux-backports-modules-nouveau-lucid-generic: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured

If anyone else has seen this I'd appreciate pointers to any explanations or solutions. Thanks.

---

### Post by Kevbert on 2010-03-12
Please open terminal and enter
```
df -h
```
It may be that your boot sector is full.

---

