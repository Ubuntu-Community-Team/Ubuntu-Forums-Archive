---
title: "Errors were encountered while processing"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by monymirza on 2010-06-11
when i update my system, it gives this error.

Errors were encountered while processing:
 libapache2-mod-php5
 php5
 php5-mysql
 dbconfig-common
 php5-gd
 phpmyadmin


i tried this also but not solve

**sudo dpkg --configure -a**


please help me

---

### Post by arrange on 2010-06-11
Could you provide more information from the [Terminal](https://help.ubuntu.com/community/GnomeTerminal)?

What does this command say?
```
sudo dpkg --configure -a && sudo apt-get update && sudo apt-get install -f && sudo apt-get dist-upgrade
```

---

### Post by monymirza on 2010-06-12
my friend is upgrading from 9.10 to 10.04. when he upgrade this error comes...

---

