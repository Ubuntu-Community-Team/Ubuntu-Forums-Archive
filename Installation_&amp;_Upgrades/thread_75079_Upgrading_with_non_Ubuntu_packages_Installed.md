---
title: "Upgrading with non Ubuntu packages Installed"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by juicewvu on 2005-10-13
I've been using Hoary on my laptop, dell inspiron 6000, since I purchased it in early May, During the time I've been using Hoary, I've found it necessary to install a few packages from source to get the latest and greatest,  The ones that really come to mind are my ipw2200 drivers and kismet.  The drivers included with Hoary were old and had to be updated in order to connect to networks using WPA for authentication.  Should it be safe to change the repos, apt-get update && apt-get dist-upgrade, or should I format and do a fresh install?

Many thanks,
Josh

---

### Post by daller on 2005-12-01
[QUOTE=juicewvu]I've been using Hoary on my laptop, dell inspiron 6000, since I purchased it in early May, During the time I've been using Hoary, I've found it necessary to install a few packages from source to get the latest and greatest,  The ones that really come to mind are my ipw2200 drivers and kismet.  The drivers included with Hoary were old and had to be updated in order to connect to networks using WPA for authentication.  Should it be safe to change the repos, apt-get update && apt-get dist-upgrade, or should I format and do a fresh install?

Many thanks,
Josh[/QUOTE]

An upgrade should be safe... But ipw2100 has to be modprobed again...
IMO a cleaninstall is the best!

---

### Post by juicewvu on 2005-12-01
Well I eventually broke down and attempted the upgrade later that day, and after a reboot all was fine.

---

