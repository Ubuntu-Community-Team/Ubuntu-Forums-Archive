---
title: "Conflict libldap2 and ia32-libs-openoffice.org"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by ebsbel on 2006-06-05
Some time ago my Openoffice stopped working. I tried a lot of stuff to get it running, including to add Debian repositories. After a while my Ubuntu system was totally unbootable. Now I have removed the Debian sources, so I only use the Ubuntu sources and I was able to fix my system and upgrade to 6.06. However I can't install Openoffice. Openoffice depends on ia32-libs-openoffice.org and this can't be installed thanks to libldap2. I get this error message:
```
Attempting to write to "/etc/ldap/ldap.conf" which is also in the package libldap2
```
I have tried to reinstall libldap2 and all kinds of packages that could be related to this. I haven't seen anyone else have this problem, so I hope someone can help me.
Thanks in advance!
E

---

