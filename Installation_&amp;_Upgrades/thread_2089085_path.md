---
title: "path"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by histanbullu on 2012-11-28
hi,
how can i delete a pathway (old pathway) from PATH? i see it with echo $PATH
thanks

---

### Post by Lars Noodén on 2012-11-28
Simply assign the new value(s) to the variable ${PATH}  It will overwrite the old values.

```

export PATH=/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games

```

---

