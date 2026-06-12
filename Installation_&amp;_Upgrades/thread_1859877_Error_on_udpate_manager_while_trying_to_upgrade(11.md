---
title: "Error on udpate manager while trying to upgrade(11.10)"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by vhmolinar on 2011-10-14
Yesterday I update my ubuntu from 10.10 to 11.04. Everything looked fine untill i reach grub. The first ubuntu option was not working. I was getting a black screen with some log failures telling me the os couldn't load some devices. To 'fix' it, i choosed previous versions>first one(dont remember the version). So ok, this time i could load into my ubuntu and perform my tasks fine. But i was still concerned about the first ubuntu version of grub which wasnt loading indeed. To fix it, i tryed to update my ubuntu version to 11.10, and then i got this message at 'Setting new software channels' in update-manager:

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug update-manager' in a terminal.

---

### Post by vhmolinar on 2011-10-20
Solution: go to Synaptic and remove 'libsublime1'.

---

### Post by hansdown on 2011-10-20
Welcome to the forum, vhmolinar.

Glad you fixed it.

---

