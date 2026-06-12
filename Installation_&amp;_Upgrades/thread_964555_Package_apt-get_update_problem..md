---
title: "Package apt-get update problem."
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Vinno on 2008-10-31
(03:25 PM)[vinno@vinno:~]$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up python-mpd (0.2.0-2) ...
pycentral: pycentral pkginstall: not overwriting local files
pycentral pkginstall: not overwriting local files
dpkg: error processing python-mpd (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sonata:
 sonata depends on python-mpd; however:
  Package python-mpd is not configured yet.
dpkg: error processing sonata (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 python-mpd
 sonata
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any, ideas how to fix this?

---

### Post by CloudFX on 2008-10-31
Try running the upgrade using the Update Manager input

```
update-manager -d
```

---

