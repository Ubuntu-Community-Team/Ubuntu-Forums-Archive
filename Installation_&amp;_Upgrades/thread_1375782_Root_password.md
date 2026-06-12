---
title: "Root password"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by Soop_ on 2010-01-08
I don't remember giving a root password.  And if I try to su to root, it won't take the only password I've ever given it.

Am I missing something?  How do I get root on my own box?

---

### Post by amauk on 2010-01-08
> **Soop_ said:**
> I don't remember giving a root password.  And if I try to su to root, it won't take the only password I've ever given it.by default, the root account has no password
meaning you cannot log in as root directly

> **Soop_ said:**
> How do I get root on my own box?
```
sudo -i
```

---

### Post by oldfred on 2010-01-09
You do not need root, you just use sudo or gksudo for any commands that need root privileges.

Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Soop_ on 2010-01-12
Great thanks you guys, that's cleared it up.

---

