---
title: "Upgrade 6.06"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by emut on 2009-11-23
Hi,

I have a box in production that is running on a older version of Ubuntu server.

```

admin@remote:/etc/samba$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.2 LTS"

```

Would it be advisable to upgrade?  The main uses of the box are:

Samba, SSH, Squid, Apache, Smokeping, Postfix/Roundcube.

The hardware is an older Dell Poweredge 1600SC with 1Gb RAM.

---

### Post by ptn107 on 2009-11-23
You can upgrade from 6.06 LTS to 8.04.3 LTS.  Make sure dapper-updates is enabled in /etc/apt/sources.list and run the following:
```
sudo apt-get update && sudo apt-get install update-manager-core -y
sudo do-release-upgrade
```
You shouldn't have any issues.  As always, though, backup first.

---

