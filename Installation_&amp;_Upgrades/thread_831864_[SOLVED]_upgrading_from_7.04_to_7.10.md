---
title: "[SOLVED] upgrading from 7.04 to 7.10"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by sirbow2 on 2008-06-17
when i try to upgrade through update manager it says their is a bug in dist-upgrade program how do i fix it? the normal update program works for system fixes etc just not dist upgrades.

---

### Post by avtolle on 2008-06-17
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) should help you.

---

### Post by sirbow2 on 2008-06-17
their is a bug in the upgrade program(says it estimate end time) so i cannot upgrade please help! and please don't give dumb answers. how do i fix the bug?!!1

---

### Post by avtolle on 2008-06-17
```
sudo aptitude update
sudo aptitude dist-upgrade
```
Try the above commands from terminal. Alternatively, post the error message here as it appears on your screen so someone can take a look at it.

---

### Post by sirbow2 on 2008-06-17
this is what happened when i tried to upgrade from 7.04 to 7.10.


Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

here is another

Getting upgrade prerequisites failed

The system was unable to get the prerequisites for the upgrade. The upgrade will abort now and restore the original system state.

Please report this as a bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

---

