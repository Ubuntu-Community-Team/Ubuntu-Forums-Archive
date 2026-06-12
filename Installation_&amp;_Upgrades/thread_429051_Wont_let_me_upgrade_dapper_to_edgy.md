---
title: "Wont let me upgrade dapper to edgy"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by g0ow on 2007-04-30
right now i have dapper...
my goal is to do dapper->edgy->feisty
since you can't go from dapper->feisty
so when i do 
gksu "update-manager -c" 
it loads up and says 6.10 is out, i try to upgrade, and then i get the error
"authenticating the upgrade failed.  there may be a problem with the network or the server."
====extra info=====

:~$ gksu "update-manager -c"
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmpDRqsWL/edgy.tar.gz'
authenticate '/tmp/tmpDRqsWL/edgy.tar.gz' against '/tmp/tmpDRqsWL/edgy.tar.gz.gpg'
exception from gpg: GnuPG exited non-zero, with code 2

---

### Post by zvacet on 2007-05-01
Better way will be to do clean Feisty install,but your choice.Try this,maybe will help you

```
sudo aptitude update && sudo aptitude upgrade
```

---

