---
title: "how to persuade mysql to start with --skip-grant-tables"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by risings0n on 2007-07-24
Why do we have to split configuration in 1000 files for every service? I want my mysql server to start with --skip-grant-tables option. It works on all standard mysql installations by adding the option to my.cnf, but not in ubuntu, i cannot find a suitable place to add the option. 

Tried: 
/etc/init.d/mysql
/etc/mysql/debian.cnf
/usr/bin/safe_mysql (added the --skip-grant-tables in line 387 and 2 lines below that, but still the server uses grant tables. 

well, it worked in window$$ (that should give a good motive to anyone who can help!!)

thankx in advance

---

