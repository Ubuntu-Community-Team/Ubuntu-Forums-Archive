---
title: "Problem upgrading ubuntu from 12.04 to 14.04"
date: 2019-07-11
forum: Installation &amp; Upgrades
---

### Post by mariem-11 on 2019-07-11
Hi,
I'm trying to upgrade my ubuntu system from 12.04 distribution to 14.04.
the command apt-get update doesn't show any error, nor the apt-get apgrade.
but when running the command do-release-upgrade , it returns this error
Failed to fetch
[http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-user-docs/gnome-user-guide_3.8.2-1ubuntu0.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-user-docs/gnome-user-guide_3.8.2-1ubuntu0.1_all.deb)
Échec de la connexion [IP : 91.189.91.23 80]
Failed to fetch
[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-170_3.13.0-170.220_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-170_3.13.0-170.220_all.deb)
Échec de la connexion [IP : 91.189.91.26 80]

---

### Post by Impavidus on 2019-07-11
Both 12.04 and 14.04 are dead. Upgrading from one dead release to another dead release, then to a release that's still alive but quite old already, is not completely impossible, but a hassle, unlikely to succeed and a bit pointless. Backup your data and try a fresh install of 18.04.

---

### Post by mariem-11 on 2019-07-11
> **Impavidus said:**
> Both 12.04 and 14.04 are dead. Upgrading from one dead release to another dead release, then to a release that's still alive but quite old already, is not completely impossible, but a hassle, unlikely to succeed and a bit pointless. Backup your data and try a fresh install of 18.04.
i cannot do the fresh install because i'm working on a remote server.
is there any way to do the upgrade from 12.04 to 14.04 and then from 14.04 to 16.04?

---

### Post by Impavidus on 2019-07-11
You can try this: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades). No guarantees it it will work.

---

