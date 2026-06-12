---
title: "Install from USB, tries to detect non-existent CD-ROM"
date: 2011-04-23
forum: Installation &amp; Upgrades
---

### Post by H4rm0ny on 2011-04-23
I'm trying to install Ubuntu Server on a new machine from a USB drive. The install fails because it keeps trying to find a CD-ROM drive which the machine doesn't have.

USB drive was created using Startup Disk Creator. The target machine correctly detects and boots from it. But then it reached then it failed at a message saying 'Couldn't detect CD-ROM hardware' (or very similar to this). After a little searching I found the boot option: **cdrom-detect/try-usb=true** . Used this and it correctly brings up my USB drive and asks if I want to use it and I confirm, but then it comes up with "Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive... Try again to mount the CD-ROM".

I can't get past this. Anyone know how to do this?

Many thanks,

H.

---

### Post by H4rm0ny on 2011-04-23
I have sort-of solved this by not using Start-Up Disk Creator.

Instead, I downloaded the latest Unetbootin. This threw the same errors at first, but selecting the Expert option for install (note from Unetbootin, not the same as the Expert CLI option on the Ubuntu install) seems to have got me past the issue. I have no idea how, however.

H.

---

