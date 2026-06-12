---
title: "Zope /etc/init.d/ script not present"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by italo46 on 2007-10-30
Hi all,

I'm running an Ubuntu Feisty Fawn and I'm trying to run a local Plone site. (I'm an Ubuntu/Debian newbie, but not a Linux one).

After installing the zope2.9 package I was trying to start it, but found that the /etc/init.d/zope2.9 file is not there, even if the rc* files point to it.

In adept-manager the list of files belonging to this package contains that file, but it is listed as empty (size zero).

Someone has already encountered this problem? Or can someone tell me how to debug the installation to see if something got wrong?

Thank you very much in advance

SOLVED: I removed the fiel before uninstalling the package :(, after a purge with dpkg and a reinstall all is working fine.

---

