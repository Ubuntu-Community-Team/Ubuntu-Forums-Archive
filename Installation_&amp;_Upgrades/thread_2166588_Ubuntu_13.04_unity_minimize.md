---
title: "Ubuntu 13.04 unity minimize"
date: 2013-08-10
forum: Installation &amp; Upgrades
---

### Post by sudo89 on 2013-08-10
Ubuntu 13.04 unity minimize how to ?

Previously I was using. But now is not working

**sudo add-apt-repository ppa:garhuy/unity**

How else can I do ?

---

### Post by sudo89 on 2013-08-11
Help ??

---

### Post by grahammechanical on 2013-08-11
You have added the garhuy/unity PPA to your software sources. Now you need to update the sources list and download and install the packages in the PPA.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

Or

```
sudo apt-get dist-upgrade
```

Regards.

---

