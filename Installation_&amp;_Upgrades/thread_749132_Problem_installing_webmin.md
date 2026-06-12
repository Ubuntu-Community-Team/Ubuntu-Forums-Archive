---
title: "Problem installing webmin"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by wira1505 on 2008-04-08
Dear all,
Somebody help me, pls.
I have problem when installing webmin 1.410 with package installer extension is .deb.
I have got warning with this messege /var/cache/apt/archieves - lock.
I have use root privilege.
tq

---

### Post by Partyboi2 on 2008-04-08
make sure you do not have synaptic package manager or add/remove open while trying to install the package. If you are still getting the var lock message and have none of the above open you could try removing the lock```
sudo rm /var/cache/apt/archives/lock
```

---

