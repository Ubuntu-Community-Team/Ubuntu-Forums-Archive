---
title: "Problems after disk error messed up /var/lib/dpkg/status"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by RageLtMan on 2010-10-12
A while back a disk error caused /var/lib/dpkg/status to go south. I managed to rebuild it with some the help of a script i found online, but now there's a package called libghc6-edison in limbo on my install. It has no sources, as it was custom built, and i cant seem to find the references to this thing. I've tried grepping all the files in /var/lib/dpkg to no avail. Any ideas where else this information could be stored? i need to find all the references to the package and purge them... Thanks

---

