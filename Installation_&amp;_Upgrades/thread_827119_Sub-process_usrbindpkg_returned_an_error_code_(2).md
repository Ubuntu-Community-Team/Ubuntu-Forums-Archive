---
title: "Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by vanvasten on 2008-06-12
Cant solve this problem!
the same error is repeated with any other install of any program y want to install!

vanvasten@ARCANGEL:~$ sudo apt-get install postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  postfix-cdb postfix-ldap postfix-mysql postfix-pcre postfix-pgsql procmail
  resolvconf sasl2-bin
The following NEW packages will be installed:
  postfix
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1160kB of archives.
After this operation, 2691kB of additional disk space will be used.
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 21937 package `libgsl0ldbl':
 `Suggests' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

