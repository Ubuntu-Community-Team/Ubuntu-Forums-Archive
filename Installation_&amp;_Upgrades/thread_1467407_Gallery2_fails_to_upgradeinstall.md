---
title: "Gallery2 fails to upgrade/install"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Artemis3 on 2010-04-30
[As described here](https://bugs.launchpad.net/ubuntu/+source/gallery2/+bug/558961), I'm unable to use gallery2 anymore:

This is what it shows in the console:
I'm getting this when trying to install the gallery2 package (System upgraded from Ubuntu 9.10):

```
LANG=C sudo aptitude install gallery2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following partially installed packages will be configured:
  gallery2
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up gallery2 (2.3-1ubuntu3) ...
ln: creating symbolic link `/usr/share/gallery2/lib/smarty': No such file or directory
dpkg: error processing gallery2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gallery2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up gallery2 (2.3-1ubuntu3) ...
ln: creating symbolic link `/usr/share/gallery2/lib/smarty': No such file or directory
dpkg: error processing gallery2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gallery2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
```

It looks like a packaging error. What to do here?

---

