---
title: "Install in new SSD"
date: 2024-10-01
forum: Installation &amp; Upgrades
---

### Post by mhortalr on 2024-10-01
Good morning. I have replaced the SSD in my computer and I want to install Ubuntu 24.04.1 LTS on it. I prepared the disk image on a USB drive and tried to start from it. 
When the installation got to the point "where do you want to install the system" it only showed partitions in my old HDD. It didn't show an option of installing it on the SSD. Do I need to do something with the SSD so that it shows as a target to install the system?

---

### Post by yancek on 2024-10-01
Do you have a hard drive in addition to the new SSD?  Did you create a partition table on the SSD?  Does the SSD have a partition table, partitions and/or filesystems on it?

---

### Post by TheFu on 2024-10-01
Desktop or laptop?  With laptops, there are some BIOS settings that usually need to be changed to be Linux friendly, like disabling Intel's RST/RAID and choosing ACHI mode.  I changed about 20 settings in a new-to-me Dell laptop before I tried to install Linux.  I think only 5 of them were actually needed.

Also, ensure the firmware for the BIOS and SSD are the latest possible.

If the BIOS doesn't see the SSD, that's 1 issue.
If the BIOS sees it, but the Try Ubuntu flash drive doesn't, that's a different issue.

---

### Post by grahammechanical on 2024-10-01
I know I sound silly but did you scroll down? A sata drive will be listed as sda with its partitions as sda1; sda2; sda3 etc. The list may extend down and be hidden by the window bottom edge. A SSD will have a different designation Non-Volatile Memory Express drives = nnme.

Make sure that you select the SSD as the location of the Grub boot files /boot. Otherwise, the installer may put the boot files on the hard drive. You may need to scroll down to see the nvme drive.

Regards

---

