---
title: "Bastille install fails with Hardy Upgrade?"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by devnulljp on 2008-05-22
Anyone else managed to get the Bastille package to install after the Hardy upgrade?
I just ugraded, and bastille crapped out during the install with this error:

```
Setting up bastille (1:2.1.1-18) ...
ERROR: "/sbin/bastille-ipchains" not available!
invoke-rc.d: initscript bastille-firewall, action "start" failed.
dpkg: error processing bastille (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bastille
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```
Anyone else?

iptables is installed not ipchains...

---

