---
title: "How do I install php-gtk 2.0.1 in ubuntu"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by Felipe Panegalli on 2012-05-23
Hello, my english is poor sorry... How do I install php-gtk2.0.1 in ubuntu 12.04?

thks

---

### Post by roelforg on 2012-05-23
I think it involves recompiling php...
```

sudo apt-get build-dep php5

```
installs all the build dependencies you need for it (this'll save you a lot of time).

---

### Post by Felipe Panegalli on 2012-05-23
It did not work, gives the error class php-gtk, the problem is that I can not install php-gtk.

---

### Post by roelforg on 2012-05-23
> **Felipe Panegalli said:**
> It did not work, gives the error class php-gtk, the problem is that I can not install php-gtk.

That is because you need a recompiled php with the right opts before you can build php-gtk.
It's all on their website.

---

