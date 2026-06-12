---
title: "synaptic package manager doesnt function after update to 8.04 lts"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by niijel on 2008-05-15
Selecting package manager or software sources from admin menu - they attempted to start then gave up without anything showing on screen.

I checked the syslog etc to no avail.

Solution: I needed to add the local machine name and IP to the host file. (hosts in network setup)

I suspect that sudo was failing because of this somewhere in a script.

odd.

If this is covered elsewhere please feel free to point readers at that info :)

---

### Post by bapoumba on 2008-05-15
[http://ubuntuforums.org/showthread.php?t=723361]("http://ubuntuforums.org/showthread.php?t=723361"), most probably :)

---

