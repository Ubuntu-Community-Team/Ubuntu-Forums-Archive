---
title: "Partitioning for root with Hoary to Breezy upgrade"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by Stang96 on 2005-11-29
I am trying to upgrade my laptop(I have a dual boot) from Hoary to Breezy, and it says that I need to make a root directory.  How do I need to repartition my drive so that it will make room for root?  How much space does root take?

---

### Post by aysiu on 2005-11-29
The root directory is the main directory where all the other ones live.
It'll have a mount point of /
Other subdirectories (if they had their own partitions) would have a mount point of /home or /boot

---

### Post by bwog on 2005-11-29
I understand that you have installed hoary, so you already have a root directory. That is strange, so perhaps you should wait with the upgrade untill we understand this.

Did you use [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes) for the dist-upgrade? You do not need to reinstall.

Can you tell us a little more about your laptop? Which partitions do you have, which OS is on it, how large are they and how are they formatted?

---

