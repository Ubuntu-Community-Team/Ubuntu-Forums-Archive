---
title: "Unable to install from USB unit"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by Valyander on 2008-11-06
I am trying to install Ubuntu 8.10 on my desktop at home, but I've run into a rather odd problem.
After having set up the installation parameters and confirming on the last confirmation window I get an error I have not seen before.

"The installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/cdrom

Please close any applications using these mount points.

Would you like the installer to try to unmount these partitions again?"

Seeing as I'm installing directly from the USB unit, and there is no drive in the CD-ROM, I can't quite see why I have this problem. Regardless of what I ask the installer to do on this dialog (didn't note what the choices were unfortunately), it heads back to the "Choose partition" part, and I'm headed into a manual-infinite-loop situation.

Anyone else run into this problem? Perhaps even have a solution? Would be deeply appreciated. :)

---

### Post by C.S.Cameron on 2008-11-06
I understand that the USB installer thinks it is a cdrom, (as It is an image from a CD).
Check where the installer is trying to install the grub loader, (I think this is the last window in setup).
It sounds like it could be trying to put it on (sdb)and not (sda), or vice versa.

---

### Post by Valyander on 2008-11-06
Hadn't thought of that. Worth a check.

---

### Post by Valyander on 2008-11-07
Can't quite see what happened, but it would almost seem that the USB stick had mounted some sort of temp storage on the disk that I was about to install Ubuntu on. And since it couldn't very well unmount the files it was about to install from, it failed. And unfortunately the logs yielded no useful information.
Also trying to install it this way messed with the boot on my Windows partition, producing a bsod on boot.
Ended up just burning an install CD.
Oh well :)

---

