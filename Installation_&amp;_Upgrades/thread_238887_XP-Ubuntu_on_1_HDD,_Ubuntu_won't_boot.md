---
title: "XP-Ubuntu on 1 HDD, Ubuntu won't boot"
date: 2006-08-18
forum: Installation &amp; Upgrades
---

### Post by digi421 on 2006-08-18
I have 4 HDDs in my system, 3 of which are a RAID0 pack. The 4th drive hosted my XP installations (32- and 64-bit versions). I have now removed the partition which had the 64-bit version on it and installed Ubuntu on it (booting from the live CD, deleted the xp64 partition, set up a 100GB ext3 partition for root and a 19GB swap partition). The installation went fine with no errors. However, when I reboot now, I only get the old Windows boot menu (with the old choices of booting either the 32- or 64-bit version). No grub, nothing else.
Attached is my partition table (as seen by XP).
Obviously what I want to accomplish is to have one boot manager (I don't really care which one, as long as it allows me to choose which OS to boot). Heck, I'd even be happy to have a boot disk for Ubuntu (most of my work is still done on Windows, but I really want to try out Ubuntu).
All 4 drives are S-ATA drives and for some reason, Ubuntu saw the system drive as sdd (though it is SATA2 in the BIOS).
So my question would be: How can I boot Ubuntu without screwing up my XP installation?

---

