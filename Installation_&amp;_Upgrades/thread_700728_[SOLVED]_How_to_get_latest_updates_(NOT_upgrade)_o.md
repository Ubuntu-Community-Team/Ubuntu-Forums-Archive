---
title: "[SOLVED] How to get latest updates (NOT upgrade) on headless server ?"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by dbyrne on 2008-02-18
As subject, how do I get and install the latest fixes on a headless server (7.10) ? I've run "sudo apt-get update" which seems to get the updates but not install them :confused:

---

### Post by miriad on 2008-02-18
sudo apt-get upgrade

This will upgrade all your current packages to the latest stable release.

Note, this is different from the sudo apt-get dist-upgrade command, which upgrades to a new distro.

---

### Post by dbyrne on 2008-02-18
Ah, that makes sense. I thought the "upgrade" arg was to upgrade to a new distro.

Thanks !

---

