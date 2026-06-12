---
title: "Ubuntu + other distro's won't see my HD on installation, OpenSuse does"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by Mirkovic on 2008-10-08
Am n00b regarding Linux.

I am attempting to install Ubuntu  on some empty space I reserved on my HD for Linux.

I have a 750 Gb Samsung SATA drive. 1 x 300 Gb Windows/NTFS, 1 x 300 Gb NTFS (intended to share files between Linux and Windows), and then 150 Gb of unpartitioned space.

Attempted OpenSuse 11 which installed fine but was not my cup op tea. Removed that distro and cleared the space with the Windows install CD.

When attempting to install Ubuntu it appears that it does not recognize my HD at all. I boot the LiveCD, and start the installation. Then a blank partition table is shown. I cannot edit it manually, there is simply no information at all in the table.

MD5 checksum is fine. Program does offer to install on USB stick if one is present. Same problem occurs with Mandriva and PC Linux.

I am particularly puzzled by the fact that OpenSuse does recognize the unpartitioned space when it is there. FYI, attempting to install "over" OpenSuse does not work, HD is still not recognized.

Other stuff: 4 Gb RAM, E8500 Dual Core, MSI P45 Neo3-FR MoBo.

It is my instinct that the solution lies in disabling IDE emulation on the motherboard, but I cannot find the way to do that (mobo book is not helpful) nor can I google my way to a solution (all topics I find on other forums describe how to reduce a windows partition to create blank space).

---

### Post by caljohnsmith on 2008-10-08
It could be a BIOS issue, but I've also seen that kind of behavior when the HDD's partition table is corrupt; I would check the integrity of the partition table since you have nothing to lose and everything to gain. :)

To check your HDD's partition table, first boot your Ubuntu Live CD, enable all your repositories in System > Prefs > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Also post the output of:
```
sudo fdisk -l
```
And we can work from there.

---

