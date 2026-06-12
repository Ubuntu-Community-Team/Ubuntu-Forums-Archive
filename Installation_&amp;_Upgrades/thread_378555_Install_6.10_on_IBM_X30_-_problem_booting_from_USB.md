---
title: "Install 6.10 on IBM X30 - problem booting from USB CD-ROM"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by neilasimmons on 2007-03-07
Hi

I'm trying to install Ubuntu 6.10 on an IBM X30 subnotebook, using a USB CD-ROM.

USB booting is enabled in the BIOS.

I have tested the Ubuntu install CD on another laptop and it works fine.

I have also tested the USB boot option on the IBM laptop by booting from a Windows setup CD and that also worked.

HOWEVER - when I put the two together and try to boot the Linux CD in the USB CD-ROM it doesn't boot from CD, instead booting straight into Windows from the hard drive.

Please could anyone offer suggestions as to what I might be doing wrong?

Thanks

Neil

---

### Post by dstew on 2007-03-07
Is the USB drive first in the BIOS boot order? Even if it is boot-enabled, in order to boot before the hard disk it has to be first in line. I think that the Windows setup CD may be bootable in a different way that doesn't depend entirely on the BIOS boot order, or else the boot order might have changed since you booted the Windows CD.

---

### Post by Nightdrive on 2007-03-31
I've had a similar problems where a disc would read, but not boot in one system, and would boot fine in another.
In the end, I reburned onto different media. Worked fine after that.

Hope this helps

---

