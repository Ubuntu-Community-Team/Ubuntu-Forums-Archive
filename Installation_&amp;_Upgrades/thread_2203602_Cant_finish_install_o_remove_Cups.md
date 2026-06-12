---
title: "Cant finish install o remove Cups"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by alek66 on 2014-02-04
Bad installation/removal left me here:

Cant completely remove or reinstall CUPS now.
```
aleza@darkstar:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up cups-daemon (1.7.0~rc1-0ubuntu5.2) ...
cp: cannot stat ‘/etc/cups/cupsd.conf.default’: No such file or directory
dpkg: error processing cups-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 cups-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I would like to reinstall.... any work arounds?

---

### Post by ajgreeny on 2014-02-04
Reinstall cups or the whole OS?

When you reinstall the OS, if that's what you mean, all the old files that are now present will be overwritten.

Use the "Something else" option at installation and you can see all your current partitions and make sure the same ones are reused for the new OS.

---

### Post by tgalati4 on 2014-02-04
There is a bug that requires avahi-daemon be installed and running for cups to work properly.  It got fixed with an update, so depending on what you did it might be recoverable.

```
apt-cache policy avahi-daemon
sudo apt-get purge cups
```

---

### Post by alek66 on 2014-02-04
> **tgalati4 said:**
> There is a bug that requires avahi-daemon be installed and running for cups to work properly.  It got fixed with an update, so depending on what you did it might be recoverable.

```
apt-cache policy avahi-daemon
sudo apt-get purge cups
```

NYET, still the same result

```
aleza@darkstar:~$ sudo apt-get purge cups
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package 'cups' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up cups-daemon (1.7.0~rc1-0ubuntu5.2) ...
cp: cannot stat ‘/etc/cups/cupsd.conf.default’: No such file or directory
dpkg: error processing cups-daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 cups-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I even stopped the avahi service

---

