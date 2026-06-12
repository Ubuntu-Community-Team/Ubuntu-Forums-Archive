---
title: "Server 9.10 upgrade crash"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by bambam82 on 2009-11-17
Today, I upgrade 2 machines to the latest version 9.10 server.
The first went fluently.
The second crashed during upgrade on phpmyadmin.
```

setting up phpmyadmin (4:3.2.2.1-1) ...
Installing new version of config file /etc/phpmyadmin/config.inc.php ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
Replacing config file /etc/phpmyadmin/config-db.php with new version
chmod: cannot access `/var/lib/phpmyadmin/config.inc.php': No such file or directory
dpkg: error processing phpmyadmin (--configure):

```

at the end it will try to fix itself by running "dpkg --configure -a".

No luck, but it said upgrade complete, but with errors.

I fix the phpmyadmin (the location only had a "/var/lib/phpmyadmin/config.inc.php.old".

Now, the question. Is it really done. If I do a "do-release-upgrade" it says there is nothing to upgrade.

All seems to be working...

---

### Post by phillw on 2009-11-17
> **bambam82 said:**
> Today, I upgrade 2 machines to the latest version 9.10 server.
The first went fluently.
The second crashed during upgrade on phpmyadmin.
```

setting up phpmyadmin (4:3.2.2.1-1) ...
Installing new version of config file /etc/phpmyadmin/config.inc.php ...
dbconfig-common: writing config to /etc/dbconfig-common/phpmyadmin.conf
Replacing config file /etc/phpmyadmin/config-db.php with new version
chmod: cannot access `/var/lib/phpmyadmin/config.inc.php': No such file or directory
dpkg: error processing phpmyadmin (--configure):

```at the end it will try to fix itself by running "dpkg --configure -a".

No luck, but it said upgrade complete, but with errors.

I fix the phpmyadmin (the location only had a "/var/lib/phpmyadmin/config.inc.php.old".

Now, the question. Is it really done. If I do a "do-release-upgrade" it says there is nothing to upgrade.

All seems to be working...

If all is working i.e. you can log onto phpmyadmin, see your dbases etc, then, yeah ... It's really done :p

Phill.

---

### Post by bambam82 on 2009-11-17
well, I was more worried about the upgrade of ubuntu than the upgrade of phpmyadmin...

---

