---
title: "Quick question, How to make a user account after initial install"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by claymore666 on 2007-05-13
as per the topic, how to make a user account after i install ubuntu? (im using ubuntustudio!)

i was not asked for root password or a user/ account password

---

### Post by taurus on 2007-05-13
Boot into recovery mode and create one with

```
useradd -m -G adm,admin,audio,video,cdrom -s /bin/bash john
passwd john
```

---

### Post by bapoumba on 2007-05-13
@ claymore666: deleted your duplicate thread.

---

