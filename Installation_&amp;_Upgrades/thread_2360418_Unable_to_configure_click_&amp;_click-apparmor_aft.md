---
title: "Unable to configure click &amp; click-apparmor after upgrade"
date: 2017-05-04
forum: Installation &amp; Upgrades
---

### Post by wand3r3r on 2017-05-04
I recently upgraded my system all the way from 12.04 to 16.04.  For the most part the upgrade went smoothly.  However there is one problem remaining.  It seems to be unable to install click and click-apparmor.  The message appears each time I attempt to install a new package.  I've tried fixing with ```
apt-get install -f 
``` & ```
dpkg --configure -a
``` to no avail.  Other forum posts talk about conflicts with other packages but this error message doesn't mention anything about that.

```

Setting up click (0.4.43+16.04.20160203-0ubuntu2) ...
router configuration specified twice
Usage: click [OPTION]... [ROUTERFILE]
Try 'click --help' for more information.
dpkg: error processing package click (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up click-apparmor (0.3.13.1) ...
router configuration specified twice
Usage: click [OPTION]... [ROUTERFILE]
Try 'click --help' for more information.
dpkg: error processing package click-apparmor (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 click
 click-apparmor
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

