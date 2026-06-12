---
title: "Computer now unbootable from floppy"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by David46 on 2007-06-11
Upgraded to Fesity.  All well, then computer suddenly refused to boot from either the floppy or CD.  This means that I am only able to start from the hard disk.  Done the obvious - boot order is correct in BIOS, checked that the disk and CD will boot in other computers.  The floppy is a LS120 - but if this is causing the floppy boot up problem I'm still baffled about the failure to boot from CD.

Can anyone make any suggestions, please?

---

### Post by dfreer on 2007-06-11
That is indeed unusual, but it is more likely to be a hardware/BIOS issue than Ubuntu. Can you try swapping in another floppy drive/CD Drive to test if they work? Reseting the BIOS might help as well.

---

### Post by ajgreeny on 2007-06-11
I'm not sure if this will help, but make sure your /boot/grub/device.map file contains the line:-
(fd0)    /dev/fd0
and then (assuming you can get into ubuntu feisty from the hard disk) try installing grub to the floppy again with the command
sudo grub-install /dev/fd0
If that works, all's well and good, but if not then I'm not sure what to tell you to do.

---

### Post by dfreer on 2007-06-11
Not really understanding why the OP would need to reinstall gub. GRUB is loaded after BIOS boots to the Hard Drive (or the floppy drive), and the OP can't get BIOS to boot the floppy or CD Drive.

---

### Post by David46 on 2007-06-12
Thanks for the advice.  The answer was in the bios - after installing Feisty I had to upgrade the bios to get power utilities to work and reset the bios in the procedure.  The defaults only gave my machine sight of the HD.  When I added into the bios setup the CD and LS120, it all works.

---

