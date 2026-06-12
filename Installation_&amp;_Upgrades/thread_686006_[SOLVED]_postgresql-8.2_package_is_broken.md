---
title: "[SOLVED] postgresql-8.2 package is broken"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by Spudgy on 2008-02-02
I'm trying to reinstall postgresql after having uninstalled it a while ago. My problem is that when I install it, it doesn't add  the init script or the /etc/postgresql directory as it did the first time I installed it, so I'm unable to run it. There is also no initdb, so I can't even set it up myself. 

How do I fix it?

---

### Post by Partyboi2 on 2008-02-02
What happens if you purge the package and install it again?
```
sudo apt-get --purge remove postgresql-8.2
```
```
sudo apt-get install postgresql-8.2
```

---

### Post by Spudgy on 2008-02-04
Yep, the purge fixed it. Thanks.

---

