---
title: "Problems with installation !"
date: 2008-04-06
forum: Installation &amp; Upgrades
---

### Post by WILL_CHAN on 2008-04-06
I tried something like :
> ~$ apt-get install libboost.*-dev libboost-doc libboost.*1.34.1
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

To install boost library but it gave me these errors ? I don't really know what's wrong ? Any one could help me out ? Thanks in advance !

---

### Post by 3rdalbum on 2008-04-06
Put "sudo" in front of it. That gives your account temporary administrator (root) privileges.

```
sudo apt-get install libboost.*-dev
```
etc.

---

### Post by WILL_CHAN on 2008-04-07
Sorry for my stupid mistake  and thanks for you help :D !

---

