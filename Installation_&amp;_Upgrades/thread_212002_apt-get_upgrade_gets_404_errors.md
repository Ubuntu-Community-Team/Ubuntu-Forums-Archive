---
title: "apt-get upgrade gets 404 errors"
date: 2006-07-09
forum: Installation &amp; Upgrades
---

### Post by snooo on 2006-07-09
Even after I've done an update...```
Reading package lists... Done
Building dependency tree... Done
The following packages will be upgraded:
  app-install-data-commercial cupsys cupsys-bsd cupsys-client language-pack-en
  language-pack-gnome-en language-pack-kde-en libcupsimage2 libcupsys2
  libcupsys2-dev libcupsys2-gnutls10 libgnomecups1.0-1 pmount
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 64.5kB/3460kB of archives.
After unpacking 2314kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Errhttp://archive.ubuntu.com dapper-updates/main libcupsys2-dev 1.2.1-0ubuntu1
  404 Not Found [IP: 82.211.81.151 80]
Errhttp://archive.ubuntu.com dapper-updates/main libcupsys2-gnutls10 1.2.1-0ubuntu1
  404 Not Found [IP: 82.211.81.151 80]
Errhttp://archive.ubuntu.com dapper-updates/main libgnomecups1.0-1 0.2.2-1ubuntu5.1
  404 Not Found [IP: 82.211.81.151 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2-dev_1.2.1-0ubuntu1_i386.deb  404 Not Found [IP: 82.211.81.151 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2-gnutls10_1.2.1-0ubuntu1_all.deb  404 Not Found [IP: 82.211.81.151 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecups/libgnomecups1.0-1_0.2.2-1ubuntu5.1_i386.deb  404 Not Found [IP: 82.211.81.151 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```Anyone know when they may get fixed?

---

### Post by FredB on 2006-07-09
Do - again ? - this :

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Maybe some not completely up-to-date repository ?

---

