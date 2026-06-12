---
title: "Uninstalling Java"
date: 2005-11-02
forum: Installation &amp; Upgrades
---

### Post by AllanP on 2005-11-02
Ok tried this: sudo apt-get remove j2re1.4.2_09  and I get this: E: Couldn't find package j2re1.4.2_09

I was in the direstory/folder (usr/local) where the above is located.

---

### Post by Xian on 2005-11-03
Try this instead:

```
$ sudo apt-get remove j2re1.4
```

If that still doesn't work then find the package name manually:

```
$ sudo apt-cache search j2re
```

---

