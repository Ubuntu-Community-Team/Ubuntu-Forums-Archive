---
title: "Apache php7_module disappeared after upgrading from 16-LTS to 18-LTS"
date: 2018-08-16
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2018-08-16
Just upgraded one of our servers  from 16-LTS to 18-LTS, which broke Apache
Looks like Apache php7_module has disappeared during the upgrade

---

### Post by edadasiewicz on 2018-08-16
I have php running ok on my server.  There is a php7.2.conf and .load in mods-enabled.  And the .load one points to /usr/lib/apache2/modules/libphp7.2.so.  I have packages libapache2-mod-php and libapache2-mod-php7.2 installed.  Maybe this will help.

---

### Post by lister171254 on 2018-08-17
I had to manually install php after the upgrade.

My point/question was that this was all working before the upgrade and it didn't after.
Should I file this as a bug/issue

---

