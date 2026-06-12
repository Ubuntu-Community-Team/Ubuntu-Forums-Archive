---
title: "Why can't I jump from LTS to LTS?"
date: 2014-11-01
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2014-11-01
I have 12.04. The upgrade instructions say update manager should let me go to 14.04 directly. But it only tells me that 12.10 is available. I don't want to upgrade from version to version four or five times. Can't I go directly to 14.04 as the instructions say?

---

### Post by Impavidus on 2014-11-01
Upgrading to 12.10 wouldn't even work, as its repositories have been taken off line.

But you can upgrade directly from 12.04 to 14.04. In the update manager, go to the settings and find the setting for "prompt for upgrade to a new ubuntu release" or something like that. The possible settings are "never", "LTS releases only" and "every release", or something like that. Set it to "LTS releases only" and it should offer an upgrade to 14.04. Right now it would be set to "every release".

Before upgrading, remember to disable proprietary drivers and PPAs (if you have any), these often cause trouble during a release upgrade.

---

