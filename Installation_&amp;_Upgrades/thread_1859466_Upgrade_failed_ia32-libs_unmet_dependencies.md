---
title: "Upgrade failed: ia32-libs unmet dependencies"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by kenbaldwin on 2011-10-13
```
sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 ia32-libs : Recommends: ia32-libs-multiarch but it is not installable
             Breaks: nspluginwrapper (< 1.4.4-0ubuntu2) but 1.2.2-0ubuntu9 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

All my sources are ubuntu oneiric.

This is a report of the same problem
[http://ubuntuforums.org/showthread.php?t=1855046](http://ubuntuforums.org/showthread.php?t=1855046)

Ideas? Thanks

Ken

---

### Post by ruj.sabya on 2011-10-14
I am receiving this error too. When upgrading from 11.04 to 11.10. Broke my update manager :(

---

### Post by Giannis_ on 2011-10-14
I have the same problem. Please if anyone knows, we need your help :)

---

### Post by kenbaldwin on 2011-10-14
Here's an official bug report:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/873883](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/873883)

The reporter says that removing ia32-libs allows the upgrade to complete. Is this a recommended workaround?

---

### Post by kenbaldwin on 2011-10-14
Removing ia32-libs worked for me.

Ken

---

