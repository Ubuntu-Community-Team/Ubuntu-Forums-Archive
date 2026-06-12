---
title: "UBUNTU and MySQL Deprecated Variables"
date: 2020-09-29
forum: Installation &amp; Upgrades
---

### Post by johnwunder on 2020-09-29
I suspect you already know this but I spent enough time on it that I don't want others to go through it.  Installation of MySQL 8 on Ubuntu 20 fails if you have deprecated variables from an old version of MySQL. I had 
query_cache_limit    = 1M
query_cache_size        = 16M
both of which are deprecated.  The error does show up in the mysql error log but shows up as a failed start in mysql service which is tried over and over after re-boot.

[https://dev.mysql.com/doc/refman/8.0/en/added-deprecated-removed.html#optvars-deprecated](https://dev.mysql.com/doc/refman/8.0/en/added-deprecated-removed.html#optvars-deprecated)

Just did not want others to lose hours like I did.
Johnny Wunder

---

