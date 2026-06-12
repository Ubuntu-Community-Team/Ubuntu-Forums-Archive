---
title: "how to get gui in ubuntu 8.04 server"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Gopal-Cbe on 2008-06-06
Can some one help me to get the gui up and running on a ubuntu 8.04 server edition.

---

### Post by iaculallad on 2008-06-06
Just **sudo aptitude install x-window-system-core gnome-core** on your terminal

and start gdm by:

```
/etc/init.d/gdm start
```

---

