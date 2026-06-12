---
title: "do-release-upgrade failed, now I can't retry"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by JoachimDurchholz on 2013-10-18
I got the system upgrade notification, started the upgrade.
Upgrade worked for a while (didn't take note of the steps, it prepared for upgrade, downloaded stuff, not sure what else), then aborted because there were too many old kernels floating around in /boot (which is a separate, 250-MB partition).
I cleaned out those old kernels from /boot. (For some reason, the package system didn't know about them, so I simply rm'ed anything with an old kernel version in it from /boot.)
I'm not getting a system upgrade notification. Okay, can happen, desktop might be fully aware of the situation.
I tried do-release-upgrade from bash. Tells me "Checking for new Ubuntu release" and "No new release found".

lsb_release -a tells me this:
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 13.04
Release: 13.04
Codename: raring

... so it SHOULD allow me to upgrade, shouldn't it?
What should I try next?

---

