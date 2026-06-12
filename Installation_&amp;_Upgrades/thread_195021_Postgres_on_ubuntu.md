---
title: "Postgres on ubuntu"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by jitesh on 2006-06-12
How do i install posgresql on ubuntu server? tried the "apt get install postgresql8.1" command, but it returned an error "Couldn't fingdpackage postgresql8.1" What do I do?

---

### Post by pertti on 2006-06-13
I just installed PostgreSQL with the same command, maybe you mispelled the package name:

```
aptitude install postgresql-8.1
```

I prefer using aptitude over apt-get, since it removes all dependencies installed with the package if you decide to remove it.

Also try an "apt-get update" before, just in case. The package is in the main repository, so you shouldn't need to enable the other repositories.

---

### Post by odyn_owl on 2006-06-13
Iinstall postgresql server, edit pg_hba.conf add own ip, but I don't now standart  password for base.
so what the standart password to PostgreSQL server?

---

### Post by pertti on 2006-06-14
I haven't really started using it, but I found [this HowTo]("https://wiki.ubuntu.com/PostgreSQL") in the Ubuntu Wiki. Hope it helps.

---

