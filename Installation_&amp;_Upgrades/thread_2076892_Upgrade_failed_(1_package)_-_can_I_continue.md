---
title: "Upgrade failed (1 package) - can I continue?"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by Kleenux on 2012-10-27
I got one problem (iptables-persistent package) during the upgrade from 10.04 to 12.04.1 

```
Errors were encountered while processing: iptables-persistent

Error in function: 
ERROR:root:not handled exception: SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

A fatal error occurred 

(...)

ERROR:root:SystemError from cache.commit(): installArchives() failed

Could not install the upgrades 

The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a). 

Setting up iptables-persistent (0.5.3ubuntu2) ...
dpkg: error processing iptables-persistent (--configure): subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing: iptables-persistent

Upgrade complete 

The upgrade has completed but there were errors during the upgrade process. 

To continue please press [ENTER]
```

I read a post that says its actually a iptables-persistent bug that shouldn't have returned an error.
(ie the upgrade is actually OK)

Question:
- can I simply ^C or reboot, and abort the recovery process?
- or should I press ENTER - (question being asked by the script)?

Thanks

---

### Post by Kleenux on 2012-10-27
Thanks for all the replies and help, appreciate it ;-)

For the ones dying to know the end of the story:

So, I killed upgrade the process and did a `dpkg --configure -a` myself: that confirmed the `iptables-persistent` package bug(?) (the post-install script returns a fatal error code).

an ```
apt-get remove iptables-persistent
``` fixed the package/updates problem, and I kept managing the iptables auto-loading at boot the same way as 10.04... perfect!

---

