---
title: "Update multiple servers to same patch level"
date: 2016-09-26
forum: Installation &amp; Upgrades
---

### Post by fendemann on 2016-09-26
Hi

I`m trying to keeping multiple Ubuntu 16.04 LTS server installations on the same update level (patch level) for a long time period.

I am familiar with the possibility to exclude packages with **apt-mark hold** from the automatic update process and update this packages to a particular version using **apt-get install less=481-2.1ubuntu0.1**. But updating all packages on all servers to dedicate versions by hand is impractical.

Is there an update mechanism or an option for apt-get, which provides the ability to upgrade a system to the latest version to test this state (system and functional tests) and then roll out this state to multiple servers ??

The ability to operate my own update repository will be eliminated because of the overhead in comparison to the number of supervising systems.

---

