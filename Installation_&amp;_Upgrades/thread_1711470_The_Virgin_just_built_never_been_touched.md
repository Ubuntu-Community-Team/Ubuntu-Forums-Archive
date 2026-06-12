---
title: "The Virgin *just built never been touched*"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by bincue on 2011-03-21
Goal: Ubuntu Studio with ~160 gB of space & 1.5 tB for drive snapshots and data storage.  

Hardware: 32bit cpu, pr0mise raid controller IDE ATA 133 ~supports 2-4 sdX's, pr0mise raid controller card SATA II ~supports 2 sdX's. 2x 80 gB Maxt0r ATA133 internal, 2x 1.5 tB WD SATA II internal.  

Intentions: Install Ubuntu Studio to the Pr0mise raid controller w/ 2-80 gB stripped =~160 gB. Mount device pr0mise raid controller w/ 2x 1.5 tB RAID 1(mirror).  

Question: [COLOR=Navy]How to map the Pr0mise raid controller ATA 133 for UBUNTU STUDIO, how to map the drives on the Pr0mise raid Controller SATA II, and how to make UBUNTU STUDIO automatically mount the SATA II mirrored device at boot (fstab edit?)?


[/COLOR]

---

### Post by bincue on 2011-03-21
This Virgin is popped.

Went through manual on alternate install instead of guided to do the stripe ~/| mirror ~/home| stripe ~swap| rebooted and did the Disk Utility to build the mirror with the storage devices. Edited etc/fstab with sudo gedit automount at boot. even added two flash drives and stripped them for swap -pri=1. When Ubuntu Studio swaps I'll be getting read 48.52 MB/Sec Avg. write 24.70 MB/Sec Avg. as high as 60 MB/Sec read and 35 MB/sec writes with them USB 2.0 thumb drives stripped created a 4GB swap if need it.

No need help, solved it.

Now it is time to put this mobo et. all in the aquarium for the next 5 years.
UBUNTU STUDIO is up and running. Lotsa storage space safely mirrored with XFS.

---

