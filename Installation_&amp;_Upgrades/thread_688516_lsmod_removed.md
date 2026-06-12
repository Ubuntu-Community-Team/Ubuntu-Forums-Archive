---
title: "lsmod removed"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by djuniah on 2008-02-05
Oops...
sudo: /sbin/lsmod: command not found

I think i accidentally removed it.  How can I restore lsmod?

---

### Post by LarryJ2 on 2008-02-05
It comes in the package module-init-tools

so  

```
sudo apt-get install module-init-tools
```

should restore lsmod  (along with others)

---

### Post by djuniah on 2008-02-05
Thanks a lot!  It seems that it was just a symlink that was supposed to be there, so i restored it after checking another system i'm running.  I'll do the reinstall of module-init-tools anyway just in case.  (I still have a few other boot snags i'm trying to smooth out)

---

