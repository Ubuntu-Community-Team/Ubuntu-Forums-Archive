---
title: "installing lime wire i got a freeze and an error......."
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by mino54 on 2008-11-03
hi all,how do i fix this




E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when I run" dpkg --configure -a"  in terminal  i get a message  "need superuser access"


thank you

---

### Post by taurus on 2008-11-03
Try

```
**sudo** dpkg --configure -a
**sudo** apt-get update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

