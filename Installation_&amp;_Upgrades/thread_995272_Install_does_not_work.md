---
title: "Install does not work"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by Dadsgé on 2008-11-27
i tried to install 'open arena' but aperantly the installation of the 'data' file doesn't work.
i always get this error
```
E: /var/cache/apt/archives/openarena-data_0.7.1-1_all.deb: probleem tegengekomen in buffer_write(fd) (10, ret=-1)
```(is in dutch, translation: problem occurred in buffer_write)

and now if i try to install updates it always give me an error.
everything goes fine till it starts to install...

```
E: /var/cache/apt/archives/openoffice.org-common_1%3a2.4.1-1ubuntu2.1_all.deb: probleem tegengekomen in buffer_write(fd) (10, ret=-1)
E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-1ubuntu2.1_i386.deb: probleem tegengekomen in buffer_write(fd) (10, ret=-1)
```(it is again in dutch, translation is the same as the above)

what should i do to get my updates and to get that game?

greetz
Dadsgé

---

### Post by Dadsgé on 2008-11-30
bump, i can't use openoffice anymore...

---

### Post by taurus on 2008-11-30
What if you clear out the cache first?

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

