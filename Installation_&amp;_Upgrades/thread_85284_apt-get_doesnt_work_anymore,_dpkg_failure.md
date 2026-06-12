---
title: "apt-get doesnt work anymore, dpkg failure"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by Sonic-NKT on 2005-11-02
Hi,
after crashing the system ;) 
apt-get doesnt work anymore if i want to install something. it says that dpkg cant read package info file in "/var/lib/dpkg/available".
how can i get this file back?
thanks bye

---

### Post by Xian on 2005-11-02
Try issuing this command:

```
$ sudo dpkg --clear-avail
```

---

