---
title: "Wont let me install anything!!!"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by bballboi288 on 2008-03-09
I just  installing the newest Ubuntu. Then I tried installing some software then restarting the system, but now it wont let me install or remove anything at all!! It wont even let me update.
This messages keeps popping up:


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

:confused:

---

### Post by Rocket2DMn on 2008-03-09
Open a terminal and run
```
sudo dpkg --configure -a
```

---

### Post by steveneddy on 2008-03-09
> **Rocket2DMn said:**
> Open a terminal and run
```
sudo dpkg --configure -a
```

and then

```

sudo apt-get update

```

then

```

sudo apt-get upgrade

```

---

