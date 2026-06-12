---
title: "NTFS Problem"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by MasterSander on 2008-04-30
When I start ubuntu, my ntfs partition doesn't mount as a default, I first have to click it and then it mounts. This is pretty stupid cause amarok for instance has to built my collection up every time again. Does anyone know how to change this? I didn't have this in gutsy.

---

### Post by tamoneya on 2008-04-30
you need to add it to /etc/fstab.  The entry would look like this if it is /dev/sda3 and it is being mounted to /windows```
/dev/sda3 /windows ntfs defaults 0 0
```

---

