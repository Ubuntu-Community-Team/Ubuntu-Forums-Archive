---
title: "swapping hdd"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by billbodewig on 2011-09-23
What happens when I swap the position of sda and sdb?

How does grub2 locate the hdd drives? By way of UUID or through its position in the bios?

For instance, suppose I install Natty on sda (first HDD) and later want to install W7 on sdb. On installing W7 the installation software looks at the bios and wants to install the OS on sda (physically the first HDD).
If I swap the two hdd physically will sda (the drive with a unique ID) now become sdb under Natty or remain as sda. Will grub look for the UUID and not sda/sdb?):P

---

### Post by YesWeCan on 2011-09-23
Grub2 searches by uuid. The drive letter is determined by the bios. So it depends on the bios but often the drive that is set to boot first is sda but sometimes the letters depend on SATA port. Because the drive letter is unreliable it is recommended to use uuid in fstab too.

---

### Post by billbodewig on 2011-09-25
OK so UUID is the main criterion when looking for the boot drive.
That makes sense since I now installed Windows on the second hard disk simply by initially swapping the two drives, setting up Windows, which sees that disk as the first one in bios, and after installation swapping them again.
Grup was updated and presto Windows loads perfectly, just using the word perfect with Windows loosely :lolflag:

During the update of windows - why does it have to log-out and -in forcing you to stay at your computer? - I just put Windows at the top in Grub.

---

