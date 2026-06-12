---
title: "help please-cdrom not reading all disks"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by neerajkumar on 2008-05-28
hello..

can someone help me out with this.

i got a message recently  after runnnin update manager.
it was lyk this.

"Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead."

can someone sort this 4 me?

---

### Post by hal8000 on 2008-05-28
Start synaptic, click on settings repositories, and uncheck the lower button for cdrom. Thats where the error comes from.

---

