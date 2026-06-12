---
title: "can edgy-backports be used on dapper server? urgent"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by g[r]eek on 2007-07-09
hello all

we deploy an application, on dapper drake server edition, that depends on postgresql-8.2 (8.1 does not work - we need 8.2's jdbc4 support).

dapper drake, with its backports enabled in sources.list, only supports postgresql up to version 8.1 - but this is not good enough.

thus we are considering temporarily enabling edgy-backports (or even feisty) in our servers so as to apt-get install postgresql 8.2. 

then, once postgres is up and running, we shall remove the backports in order to revert sources.list.

i'd like to know what implications, if any, should be kept in mind when doing this.

please note: we have considered the option of upgrading to feisty server edition, but have decided to stick with dapper. it has proven far more stable, not to mention various hardware conflicts (stalled installations) we were experiencing with feisty server.

thanks.

---

### Post by Pumalite on 2007-07-09
I would stick to repositories of the version you run; the rest is a shot in the dark.

---

