---
title: "Upgrade Servers from 9.04 to 10.04 LTS"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by Dave.Wynne on 2011-02-09
I've two servers working quite happily, but I'm aware that support for Jaunty/Jackalope is ending. One servers is a Samba PDC the other is a mail server.I obviously don't want to break either of them. What is the recommended procedure for upgrading from 9.04 to 10.04 LTS can I do it directly and if it fails can I just use my backup over the top of the upgrade to effectively downgrade?

---

### Post by dino99 on 2011-02-09
before upgrading, check a few points:

- deactivate/remove all non genuine jaunty repo (ppa & third parties)
- uninstall not required apps
- update, upgrade to get the latest packages
- clean the system as much possible: bleachbit, gtkorphan, gconf-cleaner will help
- reboot

then you can dist-upgrade:
[http://www.liberiangeek.net/2010/05/how-to-upgrade-from-ubuntu-9-04-jaunty-to-ubuntu-10-04-lucid-lynx-directly/](http://www.liberiangeek.net/2010/05/how-to-upgrade-from-ubuntu-9-04-jaunty-to-ubuntu-10-04-lucid-lynx-directly/)

---

