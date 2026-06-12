---
title: "upgrade complication"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by lux100 on 2011-02-13
When i upgraded from 10.04 to 10.10. Some of the drivers dosen't work, then i upgraded to a new kernel version 2.6-35-23-generic. All of my hardware workd. But something got  screwd. The installation dispatched to ubuntu 10.04 LTS !!!!!!!!

And when i try to upgrade again, i get this message: 

E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu
If none of this applies, then please report this bug against the  'update-manager' package and include the files in /var/log/dist-upgrade/  in the bug report." 

And in terminal i tried 

sudo apt-get update && sudo apt-get upgrade

sudo apt-get dist-upgrade

---

### Post by linuxsyst on 2011-02-13
This is a bug

---

### Post by lux100 on 2011-02-13
I know. And i cant upgrade from installation-disk

---

### Post by mörgæs on 2011-02-13
Hi, welcome to the fora.

Here is something on upgrades going awry:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

