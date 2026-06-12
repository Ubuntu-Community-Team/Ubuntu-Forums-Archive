---
title: "help with primary partitions and installation of kuibuntu!"
date: 2012-03-12
forum: Installation &amp; Upgrades
---

### Post by rubenmtz95 on 2012-03-12
hello linux users I came here as my last resource because I couldn't install kubuntu 11.10 on my pavilion g7-1260us(640GB hdd-4GB RAM-intel processor core i-3) I realized that it has 4 partitions [ATTACH]214190[/ATTACH]well the picture does not look good but here are the partitions C: NTFS 576GB primary-HP Tools fat32 3.96GB primary- Recovery NTFS 1538GB primary- system NTFS 199MB primary. Can I make another partition?or what ca I do? please help me I really want ton install kubuntu(:

---

### Post by Quackers on 2012-03-12
Welcome to UF :-)

You must not attempt to create another partition at the moment!

4 primary partitions is, as you suspect, the maximum number allowable on a MBR partitioned disc.

In order to install another operating system you will need to firstly delete a primary partition (others in your position have deleted the HP Tools partition, as you are unlikely to need them and in any event are available from the HP website).

This will free up only a small amount of space. Not enough to install Kubuntu into.
 
You can then shrink your Windows C: drive using the Windows Disk Management console - after defragmenting it first. 

At this point Kubuntu can be installed into the new unallocated space (which will automatically create an extended partition, in which you can have as many logical partitions as you wish) using the install alongside option in the installer.
Alternatively you can create the necessary partitions yourself using Gparted from the live cd and install Kubuntu into them.

If you create new partitions yourself they should be of the logical kind (NOT PRIMARY).

---

