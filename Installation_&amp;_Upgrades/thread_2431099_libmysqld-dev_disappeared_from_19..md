---
title: "libmysqld-dev disappeared from 19.*"
date: 2019-11-11
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2019-11-11
The libmysqld-dev package is part of 18.*, but seems to have disappeared from 19.*

I'd appreciate any hints as to what the packages was replaced with
Thanks

---

### Post by Xian on 2019-11-13
That package is deprecated from Eoan with the migration from mysql-5.7 to version 8.0.

---

### Post by lister171254 on 2019-11-14
Do you know where that package content moved to in V 8.0

---

### Post by Xian on 2019-11-14
There is not a drop-in replacement package from your prior installation. 

For example the libmysqlclient-dev package in Eoan has the libmysqlservices.a file from the deprecated libmysqld-dev package but it's location has changed from /usr/lib/x86_64-linux-gnu/libmysqld.a to /usr/lib/s390x-linux-gnu/libmysqlservices.a. But it is completely missing the libmysqld.a file from libmysqld-dev.

---

