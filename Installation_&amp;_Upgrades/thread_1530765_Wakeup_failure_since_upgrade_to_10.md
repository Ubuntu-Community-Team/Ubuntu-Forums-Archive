---
title: "Wakeup failure since upgrade to 10"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by dargaud on 2010-07-14
Hello all,
since upgrading to 10.04, there's been a big problem on one of my desktop PCs. when it wakes up from sleep, / is remounted read-only ! If I remove the errors=ro from /etc/fstab, the system goes to hell with all kinds of bus errors after waking up.
If I use hibernate (sleep to disk instead of RAM), it seems to work OK.
Suggestions ?

---

