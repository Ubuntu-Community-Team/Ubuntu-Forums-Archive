---
title: "[SOLVED] Check updates error"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by dnaga57 on 2008-06-15
When I try to check updates thru Sys- Admn Check updates I get the following error
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Any suggestions or help:confused:

---

### Post by Bubba64 on 2008-06-15
Have you looked in software sources to make sure the CD is ticked off and repositories or ticked on including the 3rd party conical. Software sources is located in synaptic and system-administration. It could be that all of that is enabled but your apt source list is corrupted, copy and paste this in the terminal and post it if your look through the software sources does not fix the problem.
cat /etc/apt/sources.list

---

### Post by dnaga57 on 2008-06-16
Yes ticking off CD Rom in Software sources did it
Thanks

---

