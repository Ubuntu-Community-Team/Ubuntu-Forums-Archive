---
title: "I tried to install apt-fast"
date: 2012-09-04
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2012-09-04
During installation of apt-fast the screen looped and after a while I closed the wind

sudo rm /var/lib/dpkg/lock

sudo dpkg --configure -a
Setting up apt-fast (1.7.2-1~precise1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing apt-fast (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 apt-fast


How to fix it?

---

### Post by ELMIT on 2012-09-04
I tried this:

ps ax|grep dpkg
16864 pts/6    Ss+    0:00 /usr/bin/dpkg --status-fd 147 --configure aria2:amd64 apt-fast:amd64
16865 pts/6    S+     0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/apt-fast.postinst configure 
16871 pts/6    S+     0:00 /usr/bin/perl -w /var/lib/dpkg/info/apt-fast.config configure

---

### Post by ELMIT on 2012-09-04
I killed these three apps, removed the lock file (again), purged apt-fast and it is working again, ...

Thanks!

---

