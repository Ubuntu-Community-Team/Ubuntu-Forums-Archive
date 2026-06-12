---
title: "Installing Ubuntu 5.1 with Software RAID 1"
date: 2005-11-13
forum: Installation &amp; Upgrades
---

### Post by folker on 2005-11-13
I try to install Ubuntu 5.1 with Software RAID 1.
If got a Dell SC1425 with 2 SATA disks.
During the installation I created 5 partitions on both disks formated as Linux Raid partition. (/boot / /tmp /var /home) and on both disks 1 swap partition.
After creating the partitions I created the Software RAID 1.
MD0 formated as EXT3 /boot
MD1 formated as EXT3 /
etc.
I finished the installation succesfully.
After the installation everything is working ok, but if I shutdown the system
disconnect harddrive 1 and boot again the system does not boot from disk 2.
What do I have to do to make both disk bootable?
Is this the right way to set up a Software RAID 1?

---

### Post by folker on 2005-11-18
Can anyone please help me?

---

