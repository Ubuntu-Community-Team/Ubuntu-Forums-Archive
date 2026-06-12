---
title: "Server upgrade from 18 LTS to 20 LTS hangs on mysql"
date: 2020-10-23
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2020-10-23
I've tried the upgrade a number of times and it always hangs during the mysql upgrade (see attached). There are no errors in the mysql log, but the upgrade does not continue.

I found a solution to this issue on line; the solution is to kill mysqld. Once this is done, the upgrade continues to the end.

I'd appreciate if somebody could comment on why the upgrade would hang in the first place.

Thanks,
Leo

---

