---
title: "Libraries versions mismatches"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by spibou on 2008-01-15
Hi everyone.

I tried installing libfreetype6-dev and got (not the full message)

dpkg: dependency problems prevent configuration of libfreetype6-dev:
libfreetype6-dev depends on libfreetype6 (= 2.2.1-5ubuntu0.2); however:
  Version of libfreetype6 on system is 2.2.1-5.

So the question is should I forcefully configure libfreetype6-dev
despite the version mismatch or should I upgrade ? My concern
is could upgrading break any existing packages which depend
on the versions I already have ?

Similar question with libcairo-dev:

dpkg: dependency problems prevent configuration of libcairo2-dev:
 libcairo2-dev depends on libcairo2 (= 1.2.4-1ubuntu2.2); however:
  Version of libcairo2 on system is 1.2.4-1ubuntu2.

And libpng12-dev:

dpkg: dependency problems prevent configuration of libpng12-dev:
 libpng12-dev depends on libpng12-0 (= 1.2.8rel-5.1ubuntu0.3); however:
  Version of libpng12-0 on system is 1.2.8rel-5.1ubuntu0.1.

TIA

---

### Post by spibou on 2008-01-17
Anyone , anyone at all ?

---

