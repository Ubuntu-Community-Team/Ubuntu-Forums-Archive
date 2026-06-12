---
title: "[SOLVED] Update Manager Problem"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by joethepirate on 2008-08-02
I'm running hardy heron on an XPS M1710.

My update manager is telling me that I have new update to install:
gnome-do-plugins,

When I click install updates I get the following error:

E: /var/cache/apt/archives/gnome-do-plugins_0.5.98.0-0~hardy~ppa2_all.deb: trying to overwrite `/usr/share/gnome-do/plugins/Rhythmbox.dll', which is also in package gnome-do-plugin-rhythmbox

I would really appreciate any help that you can provide. Thank you in advance.

---

### Post by hongleong on 2008-08-03
Try this:

```
sudo apt-get remove gnome-do-plugin-rhythmbox gnome-do-plugins
sudo apt-get install gnome-do-plugins
```

---

### Post by joethepirate on 2008-08-03
thank you, that seemed to do the trick.

:D

---

### Post by hongleong on 2008-08-03
You're welcomed. :)

---

