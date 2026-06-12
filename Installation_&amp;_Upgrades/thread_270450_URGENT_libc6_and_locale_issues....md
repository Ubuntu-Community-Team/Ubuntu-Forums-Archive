---
title: "URGENT: libc6 and locale issues..."
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by poncenby on 2006-10-03
Trying to install Xgl and Beryl meant upgrading the libc package on my Dapper amd64 machine.
now I'm getting in all sorts of bother with libc6 and perl complains about the locale not being supported.

can anyone tell me how to remove the newer libc6 (2.4) package and reinstall the old one (2.3_something).

i even uninstalled my nvidia driver and reinstallation is complaining about libc missing!

any help much appreciated.

poncenby

---

### Post by poncenby on 2006-10-03
fixed it by supplying apt-get with <package>=<version> details, and it successfully downgraded libc!

---

