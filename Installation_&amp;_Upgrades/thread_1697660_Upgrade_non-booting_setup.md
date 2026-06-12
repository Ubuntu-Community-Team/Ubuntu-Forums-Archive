---
title: "Upgrade non-booting setup"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by mdeen on 2011-03-01
I have an installation of Hardy which crashed. After fsck I found large parts of /etc and /lib in my lost+found and /sbin does not have quite enough programs.
I've restored /etc as well as I could but it still won't boot. The error I get while booting is
run-init: /sbin/init: No such file or directory
Kernel panic - not syncing: Attempted to kill init!
Init is present, so I assume some libs or other files are missing.

So my plan is to reinstall (and upgrade to Lucid). How can I best do this without the installation overwriting the existing files in e.g. /etc and /var ? I can't do an upgrade because the system won't boot, so I guess I'll have to use the install CD.
But if I do a clean install I have to install and configure everything else (from useraccounts to apache and mail to everything you can think of) and I'm not too keen on that.

So the question is basically: how to upgrade a non-booting system?

---

