---
title: "unable to install locales"
date: 2004-12-20
forum: Installation &amp; Upgrades
---

### Post by LKWPeter on 2004-12-20
Hello there,
I have installed ubuntu 4.10, but during package configuration there were some problems with locales, now I'm unable to reinstall it.
This is the error I get:
```
apt-get install locales
Reading Package Lists... Done
Building Dependency Tree... Done
locales is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up locales (2.3.2.ds1-13ubuntu2.2) ...
Generating locales...
  Usage:./usr/sbin/validlocale <locale>...Try `localedef --help' or `localedef -
-usage' for more information.
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on lsb; however:
  Package lsb is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 locales
 lsb
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Does anybody know what could be the reason for my problem?

---

### Post by burlap on 2004-12-20
Search the forums.
Shortcut:
```
sudo dpkg-reconfigure locales
```

---

### Post by LKWPeter on 2004-12-21
I searched the forums before and tried exactly this.
Reconfiguring the locales does *not* work, because they are not installed.
I cannot give the exact error message, because I'm not at home atm..

---

