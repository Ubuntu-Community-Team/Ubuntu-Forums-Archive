---
title: "Unable to upgrade to 14.04 by do-release-upgrade"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by Ertai87 on 2014-04-19
As title.  When I do sudo do-release-upgrade, it says no new version found.  Is there a recommended way to upgrade to 14.04, preferably without the use of peripherals?  Thanks.

---

### Post by Ubi_one_2014 on 2014-04-19
alt+f2 and type in the field:
update-manager [enter]

a windows appears that version 14.04 is available

if that does not work:
sudo apt-get install update-manager-core

and repeat alt+f2> update-manager [enter]

---

### Post by ibjsb4 on 2014-04-19
try

```
sudo do-release-upgrade -d
```

---

### Post by Ertai87 on 2014-04-20
ibjsb's solution appears to work.  Thanks.

---

