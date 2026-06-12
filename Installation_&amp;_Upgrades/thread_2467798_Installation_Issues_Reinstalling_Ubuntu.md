---
title: "Installation Issues Reinstalling Ubuntu"
date: 2021-10-08
forum: Installation &amp; Upgrades
---

### Post by bikermike2 on 2021-10-08
I am having an installation problem when I try to reinstall Ubuntu. I did my original installation and had issues after a few days and tried to reinstall. Now installation will not complete and gets hung after the "Who are you" page. Reburned a new bootable USB and tried again and the issue appears in the same place again. Any help would be appreciated.

---

### Post by MAFoElffen on 2021-10-08
First check Installation log in /var/log/installer directory... Then check the md5sum and when booted let it go through the file chocks completey, before trying to install.

That is the usually problem when it fails there... or intermittently in the install. (A bad or corrupt install image.)

---

