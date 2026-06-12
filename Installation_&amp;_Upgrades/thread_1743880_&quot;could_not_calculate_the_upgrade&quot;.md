---
title: "&quot;could not calculate the upgrade&quot;"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by emerick7 on 2011-04-29
After going from 10.10 to 11.04, in the notification area I'm getting a red-warning message circle. What does this mean, and how to I resolve it?

> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

---

### Post by emerick7 on 2011-04-30
Still haven't gotten past this. What commands can I try to diagnose this?

---

### Post by yeydrek on 2011-05-03
not working for me either

when i try to upgrade from update manager or using alternate iso i get an “calculating” error.
[img]http://www.shrani.si/f/2D/2F/1pmr6ckp/screenshotw.png[/img]

when i boot with live cd i don’t have the option for upgrade…
[img]http://www.shrani.si/f/A/2e/ha0D7by/screenshot.png[/img]

> Checking package manager
Reading package lists… Done
Building dependency tree
Reading state information… Done
Building data structures… Done
Calculating the changes
Calculating the changes
Could not calculate the upgrade
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be
caused by held packages.
This can be caused by:
* Upgrading to a pre-release version of Ubuntu
* Running the current pre-release version of Ubuntu
* Unofficial software packages not provided by Ubuntu
If none of this applies, then please report this bug against the
‘update-manager’ package and include the files in
/var/log/dist-upgrade/ in the bug report.
Restoring original system state
Aborting

---

