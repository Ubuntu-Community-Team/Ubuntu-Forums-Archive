---
title: "Upgrading 10.10 to 11.04 and getting error: Could not calculate the upgrade"
date: 2011-09-30
forum: Installation &amp; Upgrades
---

### Post by zephyrshaun on 2011-09-30
I'm trying to upgrade my version of Ubuntu 10.10 to 11.04 and I'm getting this error message:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.


As far as I know, I'm not using a pre-release version of Ubuntu. And when I look at my Repositories via Synaptic Package Manager, the ones I have checked are:

Canoncial-supported Open Source software (main)
Community-maintained Open Source software (universe)

And under Other Software:
Canonical Partners - Added by software-center

I need some help on how to troubleshoot and fix this. Any ideas?

---

