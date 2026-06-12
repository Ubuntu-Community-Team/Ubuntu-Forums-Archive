---
title: "Gutsy upgrade from Fesity ... problems, not quite there"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by BlackWoxs on 2007-11-03
Errors occurred during the upgrade process, although Gutsy is running (at least with kernel 2.6.20-16). If I try to use synaptic I get an error:

[FONT="Courier New"]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/FONT]

On trying to run 'dpkg --configure -a', I get

```
mv: cannot move `/usr/share/pmi/defaults' to `/USR/SHARE/PMI/DEFAULTS': No such file or directory
mv: cannot move `/etc/default/pmi' to `/ETC/DEFAULT/PMI': No such file or directory
dpkg: error processing powermanagement-interface (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gconf2-common (2.20.0-0ubuntu1) ...
mv: cannot move `/usr/share/gconf/default.path' to `/USR/SHARE/GCONF/DEFAULT.PATH': No such file or directory
mv: cannot move `/etc/gconf/2/path' to `/ETC/GCONF/2/PATH': No such file or directory
dpkg: error processing gconf2-common (--configure):
 subprocess post-installation script returned error exit status 1
Setting up foomatic-filters (3.0.2-20070719-0ubuntu1) ...
mv: cannot move `/tmp/foomaABS5Zs' to `/TMP/FOOMAABS5ZS': No such file or directory
mv: cannot move `/etc/foomatic/filter.conf' to `/ETC/FOOMATIC/FILTER.CONF': No such file or directory
dpkg: error processing foomatic-filters (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of foomatic-db-engine:
 foomatic-db-engine depends on foomatic-filters; however:
  Package foomatic-filters is not configured yet.
dpkg: error processing foomatic-db-engine (--configure):
 dependency problems - leaving unconfigured
Setting up libpaper1 (1.1.22ubuntu1) ...
mv: cannot move `/etc/papersize.dpkg-inst' to `/ETC/PAPERSIZE.DPKG-INST': No such file or directory
mv: cannot move `/etc/papersize' to `/ETC/PAPERSIZE': No such file or directory
dpkg: error processing libpaper1 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on foomatic-db-engine; however:
  Package foomatic-db-engine is not configured yet.
 ubuntu-desktop depends on foomatic-filters; however:
  Package foomatic-filters is not configured yet.
 ubuntu-desktop depends on powermanagement-interface; however:
  Package powermanagement-interface is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf2:
 gconf2 depends on gconf2-common (>= 2.20); however:
  Package gconf2-common is not configured yet.
 gconf2 depends on gconf2-common (<< 2.21); however:
  Package gconf2-common is not configured yet.
dpkg: error processing gconf2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-applets:
 gnome-applets depends on gconf2 (>= 2.12.1-1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-applets (--configure)
```

This continues until eventually

[FONT="Courier New"]dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.[/FONT]

Any suggestions, before I do a clean install.

---

### Post by Dark Hornet on 2007-11-03
--I had issues when I tried the upgrade feature...so I ended up backing up my /home folder, then I did a clean install....good luck.

---

### Post by BlackWoxs on 2007-11-04
Thanks - I gave up (too impatient :) and did a clean install - all seems to be working fine now.

---

