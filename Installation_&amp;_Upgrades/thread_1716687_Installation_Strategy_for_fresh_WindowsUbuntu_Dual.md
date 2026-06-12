---
title: "Installation Strategy for fresh Windows/Ubuntu Dual Boot"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by GeraldNunn on 2011-03-28
I am getting a new laptop with a 128 GB SSD as well as a 500 GB hard drive. I'm looking for some advice on strategy on partitions and installation steps. Ubuntu would be my primary operating system used for work and daily tasks, Windows is just for playing the occasional game.

My current thinking is as follows:

a. Get the GPart Live CD to create the partitions
b. Give Linux 60 GB on the SSD for "/" and Windows the rest for it's installation. Do I need a seperate partition for GRUB?
c. Put the Linux swap space on the hard drive, swap would be 16 GB to support hibernation. Laptop currently has 8 GB but may upgrade in the future
d. Split the rest of the hard drive into two partitions. A 160GB NTFS partition for installing Windows 7 games on it and the rest being an Ext4 partition for the Linux /home directory.
e. Install Windows 7 first
f. Install Ubuntu second along with GRUB which would allow me to select which to boot.

Does this seem like a reasonable plan?

---

