---
title: "dist-upgrade fail - how to remove packages with dep problems"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by vayu on 2013-11-10
dist-upgrade from 13.04 to 13.10 failed in the middle with dependency problems all related to apache and php5.  I'd like to just remove them and anything causing problems and continue with the dist-upgrade but I can't seem to remove them in the middle of a failed dist-upgrade.   It keeps getting stuck on apache2-mpm-prefork.  I think it's trying to stop the service which is not working and it just hangs there both for removing and for installing.

If I dpkg --configure -a then apt-get -f install it will hang on trying to install apache2-mpm-prefork
If I try to remove sudo dpkg --force-all --remove apache2 apache2-mpm-prefork it says:
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 312983 files and directories currently installed.)
Removing apache2-mpm-prefork ...

I can't install it and I can't remove it.
How can I continue with the rest of my dist-upgrade?

---

### Post by hamishmb on 2013-11-10
Try this:
sudo dpkg --force-all -P <your package here>

This was found here: [http://ubuntuforums.org/showthread.php?t=1597294](http://ubuntuforums.org/showthread.php?t=1597294)

I've had this once before with openoffice (partially installed).

Hopefully this'll solve it!

---

### Post by atroph on 2014-05-06
> **hamishmb said:**
> Try this:
sudo dpkg --force-all -P <your package here>

This was found here: [http://ubuntuforums.org/showthread.php?t=1597294](http://ubuntuforums.org/showthread.php?t=1597294)

I've had this once before with openoffice (partially installed).

Hopefully this'll solve it!

Hate to bump an old thread but this saved my tail when upgrading to the latest LTS. I had a package that would fail a dependency and the upgrade would not proceed any further. I used the above commands to purge the offending package (tiemu) and the rest of the upgrade ran without a hitch. Thanks!!

---

