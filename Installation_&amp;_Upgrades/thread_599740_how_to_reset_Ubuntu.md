---
title: "how to reset Ubuntu?"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by ogcub on 2007-11-01
Is there any way to reset Ubuntu to post installation state, that is remove all the packages, witch where installed by myself, not by original installer. For example i installed mythtv, during installation synaptic selected some 30 or so packages, but then i uninstall, i can only select packages with mythtv in name, so obviously lots of lib and other dependant things are left in the system, but wont be used. Or maybe there are some better tools than synaptic for this task?

---

### Post by ofb on 2007-11-01
In terminal, do: man apt-get

See clean, autoclean, & autoremove.

---

### Post by mikewhatever on 2007-11-01
You can not revert back to the original installation stage, unless you've backed it up. Use this guide to remove residual packages [http://ubuntuforums.org/showthread.php?t=500020](http://ubuntuforums.org/showthread.php?t=500020)

---

