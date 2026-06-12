---
title: "Virtual Machine issues"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by hyburn on 2010-01-07
hey folks,

Im trying to get my VM to work. it tells me the virtual box Kernal driver is not loaded, how do I get started on getting this to work

---

### Post by stew721 on 2010-01-07
> **hyburn said:**
> hey folks,

Im trying to get my VM to work. it tells me the virtual box Kernal driver is not loaded, how do I get started on getting this to work
Try this:
```
$ sudo /etc/init.d/vboxdrv setup
```

---

