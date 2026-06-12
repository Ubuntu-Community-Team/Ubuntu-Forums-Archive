---
title: "Hard drive crashed after repartitioning drive"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by Crsh on 2010-08-27
I've been attempting to install Ubuntu 10.04 onto my laptop. I used using Disk management in Win 7 to add a partition to install Ubuntu on. I ran into the problem that Windows only wants 4 partitions on a disk, which my laptop already has (HP). When I tried to add a new partition, I was forced to convert the disk to a dynamic disk. Now the computer will not start.

Before this, I accidentally installed Ubuntu to an external drive that I was trying to back up to my laptop. I should also mention that I do not have a Windows system disc.

---

### Post by oldfred on 2010-08-27
Dynamic disk is some sort of windows proprietary format. I think it still has the MBR four primary partition limit. Everyone that has had dynamic has had issues with many things adn difficulty dealing with it. I also think it is a one way conversion, but you need to check in a windows forum.

MBR partitions can have only four primary partitions. One primary can be converted to an extended that can hold many logical partitions. Windows has to be in a primary and win7 uses 2, one for a boot/recovery and another for the main system. Vendors then often use two more leaving nothing for any other systems.

[http://support.microsoft.com/kb/314343](http://support.microsoft.com/kb/314343)

---

