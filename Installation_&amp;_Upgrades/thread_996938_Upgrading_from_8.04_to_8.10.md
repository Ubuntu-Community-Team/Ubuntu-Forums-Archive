---
title: "Upgrading from 8.04 to 8.10"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by thedonpsx on 2008-11-29
I am trying to upgrade from 8.04 to 8.10 using a live CD, as when I try doing it via the update manager, I get the following errors:

W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download, they have been ignored, or old ones used instead.

When I put the liveCD into my drive, no graphic comes up saying "Upgrade", which, from other forums, I believe is supposed to happen, and I really dont want to do a clean install, as I have a tonne of software and settings etc, but if needs must...

Any help would be greatly appreciated

---

### Post by manishtech on 2008-11-29
Inert the CS,

Goto System>Administration>Software Sources
Under "Ubuntu Software" Tab, select The CD, use the check mark and then click on Close. It would ask you to reload the index. After doing this. Do the upgrade.

---

