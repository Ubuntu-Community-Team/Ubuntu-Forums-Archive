---
title: "Installing on an Intel Software RAID setup"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by filburt1 on 2007-05-12
I'm having a lot of problems installing Ubuntu 7.04 on a software RAID 0 setup.

Here's where I stand:
[list]
[*]I have an Asus P4P800 motherboard; this motherboard has the Intel ICH5R software RAID controller that allows for RAID 0 and 1.
[*]I have two Western Digital 36 GB Raptors (10,000 RPM SATA drives), set up in RAID 0.
[*]The drives are already set up in RAID 0 with Windows Vista Business installed. Before I tried to install Ubuntu, I cleared out a 10 GB space in which to create the necessary swap/ext3 partitions.
[/list]
I was hoping it would install right the first time without any intervention, but even Windows doesn't do this with this setup. So, after researching the errors I got and searching these forums, I downloaded and installed "dmraid". Running dmraid -r showed the two disks. However gparted only shows two of my IDE drives and the two Raptors individually, not as a RAID array. Strangly, the installer properly shows the devices under /dev/mapper/..., but it fails to create and format the necessary partitions with just a generic "there was an error" message referencing the /dev/mapper devices.

Any thoughts on what I should do? While browsing the list of solutions, I also came across some comments that software RAID 0 performance might be hampered due to CPU overhead to the point that it becomes pointless to use in the first place, so I might want to transfer my Vista installation to one of the Raptors and install Ubuntu on another (destroy the RAID array).

---

