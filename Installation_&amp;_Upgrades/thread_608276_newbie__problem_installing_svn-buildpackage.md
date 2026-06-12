---
title: "newbie / problem installing svn-buildpackage"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by pius1225 on 2007-11-09
Hi,

i got this problem when im installing svn package, i need some help. below are the result on my installation.

$ apt-get install svn-buildpackage
Reading package lists... Done
Building dependency tree... Done
svn-buildpackage is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 58 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up at (3.1.10ubuntu4) ...
 * Starting deferred execution scheduler atd                                                                                 invoke-rc.d: initscript atd, action "start" failed.
dpkg: error processing at (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-standard:
 ubuntu-standard depends on at; however:
  Package at is not configured yet.
dpkg: error processing ubuntu-standard (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 at
 ubuntu-standard
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thanks,
Pius

---

