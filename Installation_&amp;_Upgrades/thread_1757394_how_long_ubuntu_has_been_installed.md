---
title: "how long ubuntu has been installed"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by linuxnoob420 on 2011-05-13
im just wondering if there is a way i could see the installation date on my Ubuntu partition how long its been installed

---

### Post by malspa on 2011-05-13
If you haven't changed your username since you installed, try:

```
$  sudo passwd -S [username]
```

Gave me the exact date here, confirmed by checking my installation notes:

```
steve[~]$  sudo passwd -S steve
steve P 07/25/2010 0 99999 7 -1
```

---

### Post by linuxnoob420 on 2011-05-13
thanks man that worked like a charm

---

