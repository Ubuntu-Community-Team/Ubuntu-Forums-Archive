---
title: "Upgrade from 16.04 to 18.04 with server AND desktop installed"
date: 2018-08-27
forum: Installation &amp; Upgrades
---

### Post by stray.light on 2018-08-27
I have looked at the directions for upgrading from LTS to LTS but in my case I have Server installed (first) because I wanted mdadm for RAID and then installed Desktop for the GUI.  Given I have both, should I follow the Desktop directions for the upgrade or Server?  Or is there a different path I need to follow?  It is, of course, critical that my RAID set up not be upset.  Thank you for any advice the community can give.

---

### Post by TheFu on 2018-08-27
Backup anything you can't afford to lose, get fully patched, reboot, then run **do-release-upgrade**.

No promise that everything will be fine. Depends on how many manually installed things and .deb files and 3rd party PPAs the system uses.

---

### Post by stray.light on 2018-08-27
> **TheFu said:**
> Backup anything you can't afford to lose, get fully patched, reboot, then run **do-release-upgrade**.No promise that everything will be fine. Depends on how many manually installed things and .deb files and 3rd party PPAs the system uses.Thank you!  I have a few extra PPA's...I am using this box for general use and gaming so I have Nvidia's PPA there and I have Steam installed (trying to stay away from MS).  I'll take a look at my back up options before I go with your advice!

---

### Post by TheFu on 2018-08-27
Backups are 10% data, 10% owner/group, 10% permissions, and 60% having a validated, tested, restore procedure.
And whatever is left over is luck.

The more practice you have restoring backups successfully, the luck amount decreases.

---

