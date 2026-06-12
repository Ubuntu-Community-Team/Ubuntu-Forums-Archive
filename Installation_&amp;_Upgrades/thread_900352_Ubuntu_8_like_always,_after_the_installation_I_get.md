---
title: "Ubuntu 8: like always, after the installation I get 640x480 resolution"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by Nokao on 2008-08-25
Hi...
... I'm very surprised about Ubuntu 8, it's a wanderful OS:

However, like always, after the installation I get a 640x480 max resolution and that is very annoying.

Isn't there any method to resolve that INSTEAD of manually editing the xorg.conf files !?

There must be a way to resolve that ...

---

### Post by forger on 2008-08-25
You need to give more details, graphics card brand/model and monitor brand/model, is it an LCD monitor, do you connect it using DVI or VGA?

---

### Post by Nokao on 2008-08-25
This and a manual configuration of the monitor resolved the problem...

```
sudo displayconfig-gtk
```

Putting that in the end of the installation would be good for everyone...

---

