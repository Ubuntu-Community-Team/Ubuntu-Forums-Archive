---
title: "Added DVD Now will not boot"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by GSX550ES on 2009-12-02
I upgraded from 9.04 to 9.10 which failed miserably with flashing login prompt so I gave up & did a clean install. Everything has been fine up until now, I decided to add an extra DVD rom drive. The PC BIOS auto detects the drive but but after the boot prompt the PC just hangs with a flashing cursor in the top left of the screen. I rebooted the PC & it allowed me into recovery mode, I rebuilt the bootloader & rebooted & got the same cursor. Disconnected the drive & all works fine, I know it's a good drive as it just came out of a another machine.

A simple task like this shuold be just that simple, why is it made so hard?

Alan...

---

### Post by GSX550ES on 2009-12-04
Anybody? When I added a new hard drive I edited /etc/fstab but I can't boot with the DVD connected if that is the answer.

Alan...

---

### Post by efflandt on 2009-12-04
What type of cables are you using to connect drives?  You probably do not have the DVD drive properly jumpered (little tiny things that plug in the back) and/or it ends up inserted between instead of after current hard drive(s) or conflicts with another device (cdrom?).

If you have regular IDE cables with no indication on the plugs as to which drive is which, one drive on each cable has to be jumpered as master, that the other as slave.  If the cable plugs indicate which drive is which, then jumper the drive as cable select (CSEL).

That is probably easiest (but not necessarily fastest) if hard drives are on one cable and removable drives are on another cable.

See what your BIOS shows for drive order with that drive connected or disconnected.

---

### Post by GSX550ES on 2009-12-06
Sorry should have added the drives are SATA, or at least the 3 existing 2x HDD & 1xDVD are the 'new' DVD is an ATA with a SATA convertor, the BIOS see it correctly Make/Model etc. Pretty sure the problem lies in the BootLoader but don't know enough to cure it.

Alan...

---

