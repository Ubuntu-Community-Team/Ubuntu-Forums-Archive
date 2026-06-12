---
title: "Update Manager Fails to Download Repository Information"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by Delta 397 on 2013-05-17
Update manager notified me with a little red triangle in the Unity bar that i needed to run update manager and install new updates.  When i do this i am left with the error "Failed to Download Repository Information".  Under the details tab the code says.

```
W:Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/precise/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/freyja-dev/unity-tweak-tool-daily/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```

Any help is appreciated.

Much thanks

---

### Post by oldos2er on 2013-05-17
There's no precise support in that PPA, only the newer versions quantal, raring, and saucy, so I'd remove it from your software sources.

---

