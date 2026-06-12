---
title: "Install MySQL Server packaged in .db file"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by tominh on 2008-11-11
Anyone did have trouble while installing MySQL Server packaged in .db file?

I tried to type (under root account):

dpkg --install    mysql-server......db 

i got error message in terminal:

mysql-server-5.0 depends on mysql-client-5.0 (>= 5.0.21-3ubuntu1); however:
  Package mysql-client-5.0 is not configured yet.
 mysql-server-5.0 depends on libdbi-perl; however:
  Package libdbi-perl is not installed.

There were dependencies problems among the lib. I installed mysql-client, but the last one requires another lib, and so on. As a newbie of Ubuntu, i could not get out of this trouble.

Anyone could help?

---

