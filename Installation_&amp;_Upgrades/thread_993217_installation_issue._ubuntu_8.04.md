---
title: "installation issue. ubuntu 8.04"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by emaol98 on 2008-11-25
when i run the installation program it starts loading up ubuntu and all that.... HOWEVER: i keep gettitn the error "buffer 1/0 error on device fd0,local block 0" any cluses? been trying for 5 hours now....
the iso is fine. and the comuter top of the line. and it has run buntu before. what can the problem be?
// Emanuel

---

### Post by decard_pain on 2008-11-25
the iso may be fine ...but did it burn correctly.
i'm not sure but that looks like a read error.
try burn another disk or use a live usb

---

### Post by linux_tech on 2008-11-25
It could be having trouble with the sata, maybe with the partitioning
part of the install or writing to the drive 

I would first download a new iso , burn a new cd then run the install again to eliminate a bad download as the cause.

You should post output of -
fdisk -l

You may also try adjusting bios settings from sata mode to ide mode. You may need to experiment a bit and try different setting than you have now. There should be 3 different choices
ie
IDE mode - no AHCI, no RAID
SATA mode (sometimes called AHCI mode) - AHCI enabled, no RAID
RAID mode - AHCI enabled, RAID enabled

---

