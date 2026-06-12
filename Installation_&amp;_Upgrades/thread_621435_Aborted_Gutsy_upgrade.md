---
title: "Aborted Gutsy upgrade"
date: 2007-11-23
forum: Installation &amp; Upgrades
---

### Post by Auders on 2007-11-23
I just upgraded from 7.04 to 7.10, which was quite problematic. Halfway through, the upgrade-manager aborted after failing to install python-pyode (which IMO is quite a minor issue and shouldn't abort the entire upgrade procedure). 

The failing package was easily fixed; I just deleted .egg-info file from the python site-packages dir. However, now my system is in that infamous hybrid state between two versions.

Is there any standard way to resume the upgrade procedure, or at least get the system the way it's supposed to be?

---

### Post by Auders on 2007-11-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/pyode/+bug/164761](https://bugs.launchpad.net/ubuntu/+source/pyode/+bug/164761) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Here's the bug i filed for the failing package.

---

