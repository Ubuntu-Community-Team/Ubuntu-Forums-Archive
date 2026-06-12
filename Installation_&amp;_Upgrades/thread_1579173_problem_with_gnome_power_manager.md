---
title: "problem with gnome power manager"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by dejaaan on 2010-09-21
yesterday after i launched my laptop, with the login form i got a error message saying that "the configuration defaults for gnome power manager have not been installed correctly". I'm using Ubuntu 10.04.

i searched for some solutions and tried:

1) reinstalling gnome-power-manager
2) chmod 777 /tmp
3) mv .gconfd/saved_state saved_state.old

but none of them worked. how can i solve that?

---

### Post by sikander3786 on 2010-09-21
Did you try,

```

sudo dpkg --configure gnome-power-manager

```

Post the error message it returns.

---

### Post by dejaaan on 2010-09-22
tnx for the reply

i got:

```
dpkg: error processing gnome-power-manager (--configure):
 package gnome-power-manager is already installed and configured
```

---

### Post by dejaaan on 2010-09-22
its ok now, i fixed it. the problem was caused because of the low disk space...
thanks anyway!

---

