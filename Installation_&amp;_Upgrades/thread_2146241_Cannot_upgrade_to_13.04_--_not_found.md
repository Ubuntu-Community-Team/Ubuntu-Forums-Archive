---
title: "Cannot upgrade to 13.04 -- not found?"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by thehemi on 2013-05-17
When I run "Software Updater" from the GUI, it tells me:

The software on this computer is up to date.
However, Ubuntu 13.04 is now available (you have 12.10).

So I go ahead and click "Upgrade" and the app just closes.
Figured I will try this by hand to see about greater details.

$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"

$ sudo do-release-upgrade -d
Checking for a new Ubuntu release
No new release found

So the Software Updater knows 13.04 is released, but I cannot upgrade to it?

---

