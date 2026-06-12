---
title: "Unable to upgrade linux images (dependency issues)"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by sandyandskip on 2013-02-06
Had a full boot partition when trying to upgrade linux server using apt-get upgrade. Boot partition problem is solved, but I get the following error when trying to finish upgrade. Current image is 3.2.0-35. 

```
root@LAPP-Server-LawsonSoft:/boot# apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be upgraded:
  linux-generic-pae linux-image-generic-pae
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/4,444 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-36-generic-pae; however:
  Package linux-image-3.2.0-36-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.36.43); however:
  Package linux-image-generic-pae is not configured yet.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.36.43); however:
  Version of linux-headers-generic-pae on system is 3.2.0.37.45.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Tried to  install 3.2.0.36 using apt-get, but I got this message: 

```
root@LAPP-Server-LawsonSoft:/boot# apt-get -f  install linux-image-3.2.0.36-generic.pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-3.2.0-36-generic-pae' for regex 'linux-image-3.2.0.36-generic.pae'
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-headers-generic-pae (= 3.2.0.36.43) but 3.2.0.37.45 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```What must I do to get this working correctly?

---

