---
title: "Packages not being upgraded during install"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by hovis on 2012-08-16
Hello, I am pre-seeding an install of Ubuntu 12.04 (amd64) from CD.  I have specified the following in my preseed file:-

```
d-i pkgsel/upgrade select safe-upgrade
```

Immediately after the install has completed and I have rebooted into the new system, executing:-

```
apt-get update
apt-get upgrade
```

I still see a bunch of several package updates.

I was expecting given the 'safe-upgrade' (or 'full-upgrade' which I have also tried) setting in the installer, for it to update from the Internet during initial package installation.

Am I miss understanding something here?

---

