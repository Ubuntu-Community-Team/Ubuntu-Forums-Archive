---
title: "ide-generic missing in 9.10, IDE CD-ROM issue"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by phshirk on 2009-11-30
Bought a barebones kit with Gigabyte G41M-ES2L, an Intel dual core, 1 500GB Sata and am using a fairly new IDE CD/DVD RW from system I am replacing.

CDROM is not seen by OS but is seen by the bios.
I am able to see a single IDE HDD but can not see 2 IDE HDD's
I am not able to see CDROM.

history:
Had IDE HDD from old system with 8.04 on it - up graded to 9.10. Can't see CDROM.
Removed IDE disks and tried just seeing the CDROM - can't see IDE CDROM
Loaded 8.04 on new Sata HDD and upgraded to 9.10 - can't see IDE CDROM

Been thru lots of the helps
I modified the fstab to go to /dev/cdrom - but that does not exist
/dev/hda does not exist
/proc/cdrom does not exist

modprobe -v ide-generic  - does not find module
modprobe -v all-generic-ide  - does not find module

How/where do I get ide-generic so I can load it???
And how do I make this a permanet fix?

---

