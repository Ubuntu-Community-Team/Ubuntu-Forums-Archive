---
title: "Package Operation Failed"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by xXzeppelinXx on 2010-09-04
So I've looked at all the threads dealing with this and none of it works.  

Let me tell you how it happened.  I was installing biblememorizer when ubuntu crashed.  Since then I can't install or uninstall things without this message popping up saying "Package Operation failed".  It says Biblememorizer is installed, and it runs, but when I uninstall it says this:

```
installArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 135174 files and directories currently installed.) 
Removing biblememorizer ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for python-support ... 
Setting up man-db (2.5.7-2) ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 man-db 
Setting up man-db (2.5.7-2) ... 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
dpkg: error processing man-db (--configure): 
 subprocess installed post-installation script returned error exit status 1 

```So if anyone can help me get rid of this nuisance, it will be much appreciated.

---

### Post by xXzeppelinXx on 2010-09-04
Fixed, I booted Ubuntu recovery mode, and it fixed the broken packages.  What are the odds of that?

---

