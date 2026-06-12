---
title: "Building own deb-package, problem with &quot;Provides&quot;"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by C38a7r1zvl on 2005-08-03
Hi everybody,

I make heavy use of MySQL to store information for programs like Postfix or Proftpd. I compile my own MySQL while I use the Ubuntu packages for postfix & proftpd. Both depend on libmysqlclient-packages so I put "Provides: libmysqlclient10, libmysqlclient12, mysql-common" in the control file for my custom MySQL package. For courier-authmysql, postfix-gld and postfix-mysql that works but proftpd-mysql still wants me to install libmysqlclient10. Of course I could just ignore that but.. there gotta be another way :)

Thx in advance,
Niels.

---

### Post by C38a7r1zvl on 2005-08-03
Apparently proftpd-mysql doesn't acceppt all libmysqlclient10-packages but depends on libmysqlclient10 (>= 3.23.56). Since a normal package can't provide a versioned virtual package offhand, I just created a dummy package to satisfy proftpd-mysql's needs. So consider this issue resolved :roll:

---

