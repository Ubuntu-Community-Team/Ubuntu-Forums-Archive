---
title: "Migration from 9.10 to 10.4"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by carcella on 2010-05-02
I migrated from 9.10 to 10.4 during the package installation I have the error: E: resolvconf: il sottoprocesso vecchio script di post-installation ha restituito lo stato di errore 1 ( In italian because I install the Italian version).
The problem is: the file /etc/resol.conf I can't modify or delete from all user, root also.
How is possible that?

---

### Post by zvacet on 2010-05-02
I don´t know will this help but try t otype inn terminal

```
sudo dpkg --configure -a
```

---

