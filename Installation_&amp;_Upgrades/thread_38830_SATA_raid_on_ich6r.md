---
title: "SATA raid on ich6r"
date: 2005-06-02
forum: Installation &amp; Upgrades
---

### Post by mozzi on 2005-06-02
Hallo all
Sorry for crossposting here but I am getting a little desperate now.
I have an Intel motherboard here with an ich6r sata raid chipset on when not using raid everything works fine, when activating raid I see the dvdrom in the bios and kubuntu boots from the cd.
However when it detects the cdrom in the install I get the message:
"No common CD-ROM drive was detected" trying to manually select a module doesn't work either.
My raid looks as follows:
disk 0 & 1 =raid 1 (mirrored)
disk 2 =striped (only option there)

Any ideas?

Mozzi

---

### Post by alastair on 2005-06-02
If the "hardware" (not really) RAID doesn't work - forget about it. Linux s/w RAID works very well and is just as quick. Turn RAID off - you can partition the 2 separate disks and put then in RAID as part of the install.

---

