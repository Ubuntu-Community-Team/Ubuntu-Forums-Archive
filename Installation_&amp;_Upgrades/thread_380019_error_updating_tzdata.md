---
title: "error updating tzdata"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by glederfein on 2007-03-09
Hi!
I'm trying to update my system and all updates go fine except for one: tzdata. I get the following error:
```

W: Failed to fetch http://il.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2007b-0ubuntu0.6.10_all.deb
  404 Not Found [IP: 192.116.202.128 80]

```
Can somebody please help me fix this problem?

---

### Post by bapoumba on 2007-03-09
Hello, try to change the repository (remove the il. for ex).

---

### Post by Kateikyoushi on 2007-03-09
Before upgrading update the repository list, maybe a newer version is avaible of the package you are trying to download.

```
sudo aptitude update
```

---

### Post by glederfein on 2007-03-12
> **bapoumba said:**
> Hello, try to change the repository (remove the il. for ex).
I tried changing all my repositories from "il." to "fr." and it worked!
I guess the package just doesn't exist on the Israeli server...

---

### Post by Kateikyoushi on 2007-03-12
I couldn't find anything on the server actually.

---

