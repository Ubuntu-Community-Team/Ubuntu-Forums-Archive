---
title: "Is it safe to do dist-upgrade?"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Eestlane on 2009-09-16
Latest dist-upgrade at this moment will do this:
> The following NEW packages will be installed:
  aptdaemon python-aptdaemon python-webkit software-store
The following packages will be upgraded:
  ubuntu-desktop


I would like to test that software-store. Has anyone tried this upgrade?

EDIT: Nah, I did it anyway. Haven't rebooted, so everything works atm.

---

### Post by psyke83 on 2009-09-17
> **Eestlane said:**
> Latest dist-upgrade at this moment will do this:


I would like to test that software-store. Has anyone tried this upgrade?

EDIT: Nah, I did it anyway. Haven't rebooted, so everything works atm.

Rule of thumb with dist-upgrades:

If no packages are to be removed, allow the upgrade.
If packages are to be removed, do not allow the upgrade *until* you have made certain that each package to be removed is supposed to be removed, rather than due to a temporary dependency problem.

See: [http://ubuntuforums.org/showthread.php?t=1268702](http://ubuntuforums.org/showthread.php?t=1268702)

---

