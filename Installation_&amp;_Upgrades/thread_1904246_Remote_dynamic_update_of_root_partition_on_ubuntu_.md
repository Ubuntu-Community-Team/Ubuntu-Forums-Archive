---
title: "Remote dynamic update of root partition on ubuntu installation"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by klausmedk on 2012-01-04
Hello!

I'm looking into the possibility of how to remotely and dynamically updating/switching the entire root partition of an ubuntu installation.

I have been thinking about the following scenario:
1: The remote client has in effect two root partitions with each a separate ubuntu installation.
2: The system boots from one partition which is the "active" one.
3: The other partition which is the "standby" partition is not used.
4: To update the root partition download a new partition image and install the image on the "standby" partition.
5: Update Grub to boot on the standby partition.
6: Reboot 
7: The system boots and the "standby" partition is now the "active" partition.

Is this the the way to do it?
Is there other and better ways to do it?
Can anybody point in direction of documentation?

Regards
Klaus Jacobsen

---

