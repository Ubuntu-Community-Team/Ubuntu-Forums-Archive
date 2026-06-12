---
title: "upgrading kde from kpackagekit"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by mahmoodn on 2010-12-20
I have installed kubuntu 10.10 that has kde 4.5.1. Now I want to upgrade to the latest version (I think 4.6) through kpackagekit. How can I do that? kpackagekit doesn't say anything about upgrades.

---

### Post by Zorael on 2010-12-21
Maverick (10.10) ships with KDE 4.5.1, and no other versions of it will be officially released during its lifetime. However, the Kubuntu team provides unofficial backports of later releases through the **[Kubuntu PPAs](https://launchpad.net/~kubuntu-ppa)**. There are several release channels there with varyingly recent releases. So it really depends on how much on the (potentially unstable) bleeding edge you want to be.

4.6 hasn't been released yet, but the 4.6 beta (4.5.85) is available at the time of writing on the beta backports ppa.

```
$ sudo add-apt-repository ppa:kubuntu-ppa/beta
$ sudo apt-get update
$ sudo aptitude full-upgrade
```

---

### Post by mahmoodn on 2010-12-22
Thanks for that

---

