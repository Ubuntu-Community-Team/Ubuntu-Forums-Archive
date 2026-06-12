---
title: "Ubuntu installer moves logical volumes out of extended to make primary partitions"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by malayalees on 2009-11-15
Before installing Ubuntu 9.04 (Jaunty), I had three primary partitions, followed by an extended partition with three logical volumes. The latter two partitions were empty, with the sizes 9GB & 4GB. All these were created from Win7 RC.

[[IMG]http://img687.imageshack.us/img687/9384/ubuntuinstallerchangesl.png[/IMG]](http://img687.imageshack.us/my.php?image=ubuntuinstallerchangesl.png)

In the live CD installer, I chose custom install and split the 9GB one into 7GB for root partition and 2GB for swap, and assigned the 4GB logical volume as /home.

After installation, when I rebooted, all the linux partitions seem to be outside the extended partition, as their own primaries! How can a disk have more than three primaries? It already had three primaries before the extended one. Now there are the first three primaries, followed by the extended one with a single logical volume, and three more primaries - root, swap & home! Even if the four primary-per-disk limitation (3 primary + 1 extended) has been removed, why is the installer doing this?

---

