---
title: "rsync fails to install right"
date: 2011-11-28
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-11-28
Maybe the session will be self explanatory (the highlighting is mine):```
dirac/root/c0 /root 131# apt-get install rsync
Reading package lists... Done
Building dependency tree
Reading state information... Done
rsync is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up rsync (3.0.6-1ubuntu1.1) ...
 * Restarting rsync daemon rsync
 * rsync daemon not running, attempting to start.
 * **missing or empty config file /etc/rsyncd.conf**
   ...fail!
invoke-rc.d: initscript rsync, action "restart" failed.
dpkg: error processing rsync (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 rsync
E: Sub-process /usr/bin/dpkg returned an error code (1)
dirac/root/c0 /root 132#
```I did uninstall rsync to be able to do an install of another package, which did succeed once rsync was not present.  Now installing rsync back shows the same error that happened with the other package before rsync was removed.

Shouldn't the config file be part of the package?  Or is there another package to install?

---

### Post by Skaperen on 2011-11-28
This was resolved on IRC by milamber@#ubuntu@freenode.  It apparently needed "apt-get clean" after an uninstall/purge.  Still no idea why it was doing that.

---

