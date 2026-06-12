---
title: "Ubuntu 10 won't install libmysqlclient15-dev"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by Chernevik on 2011-02-21
I'm trying to install MySQLdb for Python from source, but when I run setup.py build I get "mysql_config not found".  I try to import libmysqlclient15-dev, but I'm told "not available" and it's replaced by mysql-doc-5.0.  I install that, I already have the most recent version . . . mysql_config still doesn't work.

This is on Ubuntu 10.  I've actually installed libmysqlclient15-dev on a Ubuntu 8 box, and on a Debian box, just yesterday.

I've also tried install python-mysql ("couldn't find") and python-mysqldb ("has no installation candidate").  

Any help appreciated.

---

### Post by Chernevik on 2011-02-21
The problem was in /etc/apt/sources.list, which for some reason had all the source lines commented out.  Reversion to an older copy with active entries solved the problem.

I had remembered this board being a little more helpful than it has been lately.

---

