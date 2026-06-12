---
title: "Using an APT Proxy to install Ubuntu Server 10.04 and newer"
date: 2011-01-03
forum: Installation &amp; Upgrades
---

### Post by gnagnibu on 2011-01-03
I notice that in Ubuntu 10.04 it's not longer possibile to select local repository to download packages during installation.
Is there a way to use local respositories?

Thanks to all, bye!

---

### Post by WthIteh on 2011-01-03
> **gnagnibu said:**
> I notice that in Ubuntu 10.04 it's not longer possibile to select local repository to download packages during installation.
Is there a way to use local respositories?

Thanks to all, bye!
I'm not sure, but logically it should work in this way:
   Before running installer, in the live system, edit your sources file by
```
sudo gedit /etc/apt/sources.list
```
and change repositories addresses to your local repo.

---

### Post by gnagnibu on 2011-01-03
Ubuntu Server Installation has no live session.
I know that in previous release it asked you which repositories you prefer, but not in this one...

---

### Post by WthIteh on 2011-01-03
> **gnagnibu said:**
> Ubuntu Server Installation has no live session.
I know that in previous release it asked you which repositories you prefer, but not in this one...
OK, could you open a new tty session during installation by Ctrl+Alt+F1  ?

---

### Post by gnagnibu on 2011-01-03
Yes, but there isn't any /etc/apt/sources.list

---

