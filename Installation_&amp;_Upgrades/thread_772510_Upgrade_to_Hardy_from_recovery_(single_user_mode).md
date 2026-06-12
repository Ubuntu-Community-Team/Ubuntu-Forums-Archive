---
title: "Upgrade to Hardy from recovery (single user mode)"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by rocksocke on 2008-04-28
Hi!

i really want to upgrade to hardy, but its not working due to my personalized installation of my nvidia-graphics card via envy.

/var/log/dist-upgrade/main.log says:

2008-04-28 17:27:07,115 DEBUG The package 'nvidia-glx-new' is marked for removal but it's in the removal blacklist
2008-04-28 17:27:36,237 ERROR Dist-upgrade failed: 'Ein grundlegendes Paket müsste entfernt werden'

Which freely translated means: "A basic package would have to be removed"

this package is installed by envy. so my question is:


Can i upgrade to Hardy from the recovery mode?


thanks!

---

### Post by rocksocke on 2008-04-28
i deinstalled the restricted-drivers-common package and its dependencies (nvidia-glx-new) and now the update works. hopefully my system boots after the upgrade :)

lets try!

---

