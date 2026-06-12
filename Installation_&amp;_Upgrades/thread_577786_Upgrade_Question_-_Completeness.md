---
title: "Upgrade Question - Completeness"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by corvock on 2007-10-16
So when i run an upgrade does it simply upgrade the installed packages to the current version? I have seemed to notice my laptop (fresh install) has some items installed that my work desktop (upgrade) doesn't. 

I'm guessing that the upgrade does not install "new" packages in the new distro that would be installed to a new system? 

If this is the case, is there a way to upgrade, then catch those uninstalled packages and install them also? 

or am i just way off base?

---

### Post by perlluver on 2007-10-16
you can use sudo apt-get update, then run sudo apt-get upgrade.  Or you can use the update manager.  That should update all your packages.

---

