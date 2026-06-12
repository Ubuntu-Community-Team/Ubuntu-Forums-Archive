---
title: "How to install individual package from CD?"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by hopestorm on 2007-01-25
Now that my networking is totally gone.

I can only install new package from CD (if they exist there).

---

### Post by aysiu on 2007-01-25
```
sudo apt-cdrom add
sudo aptitude update
aptitude search *partialnameofpackage*
sudo aptitude install *packagename*
```

---

### Post by hopestorm on 2007-01-26
Thanks!!

---

