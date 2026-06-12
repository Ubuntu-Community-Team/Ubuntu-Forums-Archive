---
title: "Dependency errors on dist-upgrade"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by Gobbla on 2005-10-18
This error occurs during my dist-upgrade...

freely translated:
dpkg: dependency problem makes a configuration of ubuntu base impossible: buntu-base is dependant of ubuntu-minimal, but:
Package ubuntu-minimal is not installed.
ubuntu-base is dependant of ubuntu-standard, but:
Ubuntu-standard is not installed.
dpkg: error when handling ubuntu-base (--configure):
dependency problem, leaving unconfigured
Error occured when handling:
ubuntu-base
-------------------------------------------------------------
```
sudo apt-get install ubuntu-base ubuntu-desktop
``` and ```
sudo apt-get -f install ubuntu-base ubuntu-desktop
``` doesn't work... It lists loads of packages that depends on those but won't, for some reason, install them.

---

### Post by mlomker on 2005-10-18
The repos have been a little busy/flaky lately.  Have you [edited the default list]("http://www.ubuntuforums.org/showthread.php?t=76132")?

You could also try one of the[ other mirrors]("https://wiki.ubuntu.com/Archive").  I actually set up [my own mirror]("http://www.ubuntu.com/download/mirror/document_view") at work last weekend (30-110 Gb of disk space).  :D

---

