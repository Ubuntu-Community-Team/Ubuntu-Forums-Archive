---
title: "failed to start session"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-08-17
Just did an inplace upgrade from 12.04 to 14.04 on an hp/compaq dx2200 using update manager.  Everything looked okay until login screen came up.  Entered my password and got "failed to start session".  Went to my secretary's login and got same thing.

What is solution?

John

---

### Post by cigtoxdoc on 2014-08-17
I am surprised no one sent the correct answer, which I found on askubuntu.  need to run sudo apt-get install ubuntu-desktop.  Apparently the upgrade routine does not install ubuntu-desktop.

John

---

