---
title: "Install windows, ubuntu 12.04 and ubuntu 14.04 together"
date: 2014-10-07
forum: Installation &amp; Upgrades
---

### Post by SchrodingerCat on 2014-10-07
Hi,
for some reasons i need to have windows 7, ubuntu 12.04 and ubuntu 14.04 running on my laptop. 
Would that be possible? Could you please give me a step-by-step answer?
I kind of was concerned on how the partitions should be...
thank you

p.s. now i have ubuntu 12.04 but need to format it as well

---

### Post by Dennis N on 2014-10-07
Basic steps on a single disk:

First, find the necessary space on your disk for the new Ubuntu OS. Use a continuous block of unallocated space that might be there, or you will have to shrink an existing partition to create some. Prepare the new partition for the new install before beginning the install - use gparted from the live media to do that. Create one new ext4 partition from the unallocated space is all that is really needed. The existing swap will be used by both Ubuntus.

When beginning the install, use the "something else" option in the installer for installation type. Select the new partition, and use the "change" button set it up as ext4, mount as /, and format. If your disk is sda, install grub to "sda" 

Then proceed with the installation.

---

