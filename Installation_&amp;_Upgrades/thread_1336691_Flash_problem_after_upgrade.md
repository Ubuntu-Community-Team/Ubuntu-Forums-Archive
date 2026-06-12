---
title: "Flash problem after upgrade"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by Diverted Income on 2009-11-24
After upgrading to 9.10, I seem to have a flashplugin-nonfree problem. Cant seem to fix it or remove it.


The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 29 not upgraded.
1 not fully installed or removed.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing flashplugin-nonfree (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)




What am I doing wrong???
Thanks!

---

### Post by prcoy on 2009-11-24
check here:
[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/412944](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/412944)

in a nutshell:
You need to delete this file as root:
rm /var/lib/dpkg/info/adobe-flashplugin.prerm

---

### Post by Diverted Income on 2009-11-24
Got it fixed - Thanks!

---

