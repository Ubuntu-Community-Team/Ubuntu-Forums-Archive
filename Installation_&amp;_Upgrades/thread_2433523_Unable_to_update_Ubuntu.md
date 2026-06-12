---
title: "Unable to update Ubuntu"
date: 2019-12-20
forum: Installation &amp; Upgrades
---

### Post by DebilMudak on 2019-12-20
Running ```
sudo apt-get update && sudo apt-get upgrade
``` returns the following error
```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up libpam0g:amd64 (1.3.1-5ubuntu1.19.10.0) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package libpam0g:amd64 (--configure):
 installed libpam0g:amd64 package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 libpam0g:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
What could be the issue?

EDIT: This actually prevents me from installing anything at all.

---

### Post by yetimon_64 on 2019-12-20
```
/var/cache/debconf/config.dat is locked by another process
```
From [https://wiki.ubuntu.com/DebuggingInstallationIssues](https://wiki.ubuntu.com/DebuggingInstallationIssues) "section 3 part 3", you can use "fuser -v" to find the locking process. Also fuser has an option "-k" to kill the locking process available.

So you could try ...
```
sudo fuser -v -k /var/cache/debconf/config.dat
```
... to try and kill off the process locking the config file "/var/cache/debconf/config.dat" and then try the update/upgrade process again.

---

### Post by DebilMudak on 2019-12-20
> **yetimon_64 said:**
> ```
/var/cache/debconf/config.dat is locked by another process
```
From [https://wiki.ubuntu.com/DebuggingInstallationIssues](https://wiki.ubuntu.com/DebuggingInstallationIssues) "section 3 part 3", you can use "fuser -v" to find the locking process. Also fuser has an option "-k" to kill the locking process available.

So you could try ...
```
sudo fuser -v -k /var/cache/debconf/config.dat
```
... to try and kill off the process locking the config file "/var/cache/debconf/config.dat" and then try the update/upgrade process again.

Thanks. That worked.
Any idea what this might be:
```
                     USER PID ACCESS COMMAND
/var/cache/debconf/config.dat:
                     root       6269 F.... frontend

```

---

### Post by yetimon_64 on 2019-12-20
> **DebilMudak said:**
> Thanks. That worked.
Any idea what this might be:...


No idea sorry, I just googled the error you posted and researched a bit and came across that ubuntu wiki debugging information with the same error listed :). Glad that worked for you. Cheers, yeti.

---

