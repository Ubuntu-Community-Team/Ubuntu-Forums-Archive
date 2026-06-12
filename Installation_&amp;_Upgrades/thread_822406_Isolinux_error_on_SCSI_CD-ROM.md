---
title: "Isolinux error on SCSI CD-ROM"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by Joe Driller on 2008-06-08
Hi all.

I am trying to install Ubuntu 8.04 i386 on my old PC a dual PIII 500 Mhz with 3 SCSI disks on an ADAPTEC AHA 2940 and a SCSI CD too (in fact 2, a CD and CD-RW) on the same controller. My problem is:

I can boot from CD-ROM and get this message:


ISOLINUX 3.36 Debian-2007-08-30 isolinux:
Can't boot from this CD. Please use CD2 or try a BIOS update


I can figure that is a problem with my ADAPTEC bios and ISOLINUX but I have no idea how to solve it.
My ADAPTEC bios version is 1.23 and I don't know any new revision for this hardware.

Any one know another way to boot my system and install Ubuntu?


Thanks in advance.

---

### Post by Pumalite on 2008-06-08
Take a look at this. See if you can use it:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by Joe Driller on 2008-06-09
Thanks a lot. I seems pretty useful for me. In the next two days I'll try it and post a replay.

---

### Post by Joe Driller on 2008-06-09
I've  taken a look to UNetbootin but I understand that you need to have installed either Win or Linux previously to use the software so I can do a fresh installation with this tool.

I've tried to boot from a USB external Cd-Rom but the bios won't recognize it so my only solution is to boot from a standard IDE Cd-Rom but I don't want to keep this unit on the system forever because I am planning to use the four IDE ports to setup another RAID 10.


Any suggestion are welcomed.

---

