---
title: "Ubuntu 18.04 to 22.04 - Site went White"
date: 2023-02-06
forum: Installation &amp; Upgrades
---

### Post by Rui_Brcia on 2023-02-06
Hi all,

I upgrande my Ubuntu Server from 18.04 to 20.04 and then 22.04. It went well but my site now have a white wordpress page and do nothing.

What have i done wrong? What i'm missing in here?

sudo systemctl start php8.2
Failed to start php8.2.service: Unit php8.2.service not found.

sudo a2enmod php8.2
Considering dependency mpm_prefork for php8.2:
Considering conflict mpm_event for mpm_prefork:
Considering conflict mpm_worker for mpm_prefork:
Module mpm_prefork already enabled
Considering conflict php5 for php8.2:
Module php8.2 already enabled

/etc/apache2/mods-enabled$ ll php*.*
lrwxrwxrwx 1 root root 29 fev  6 20:13 php8.1.conf -> ../mods-available/php8.1.conf
lrwxrwxrwx 1 root root 29 fev  6 20:13 php8.1.load -> ../mods-available/php8.1.load
lrwxrwxrwx 1 root root 29 fev  6 20:31 php8.2.conf -> ../mods-available/php8.2.conf
lrwxrwxrwx 1 root root 29 fev  6 20:31 php8.2.load -> ../mods-available/php8.2.load

&#9679; apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enable

Best Regards

---

### Post by TheFu on 2023-02-06
There were a few major upgrades during that period.  Your settings will manually need to be modified to support each upgrade change.  There's no automated too for this and the upgrade process doesn't to it.  You are expected to read the release notes for the OS and each part of the server software stack that is changing and use your judgement for what changes need manual config updates.

BTW, a single LTS-to-LTS upgrade can work, but by the 2nd one, it is time to start with a fresh install and reload everything.  This will clean up some cruft that is always left over and prevent having mixed subsystems from 3 different LTS on the same server install.

Hopefully, you are using virtual machines, so it isn't hard to start over if a mistake is made.

---

### Post by ActionParsnip on 2023-02-07
Try:
```

sudo systemctl daemon-reload

```
May help

---

