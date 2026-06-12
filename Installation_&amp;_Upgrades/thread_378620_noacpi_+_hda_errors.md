---
title: "noacpi + hda errors"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by sholsinger on 2007-03-07
Hi,
I'm trying to install Ubuntu Edgy (6.10) on my machine.  I'm having problems booting with the CD.  I can't even run the CD check utility.  It tells me that i should use the "noacpi" option, but I can't do that with the CD check utility.  So I tried booting the CD normally with the noacpi option on.  I get errors like this:

```

[   201.5896436] ide_intr: huh? expected NULL handler on exit
[...] handler I/O error on device hda, logical block 353610

```
[IMG]http://www.elklighting.com/stv/UBUNTU-errors.jpg[/IMG]

This goes on and on and often moves on to block 35608 or 35609 but comes back to each block over and over again.

I was wondering why this may be?

PC Specs:
Gigabyte GA-M57SLI-S4
Athlon 64 X2 4600 (AM2)
xfx GeForce 7800GS
2 Gb of GEIL DDR2 800
320 Gb SATA HDD (3 partitions: windows | storage | unpartitioned [meant for ubuntu])

Now I know that its more difficult to install linux AFTER installing windows, but I've done it before.  I just have never tried to install any distro on such new hardware.  Is this a problem with the PCI-E bus?  Possible BIOS problems?

Thanks,
Steve

---

### Post by sholsinger on 2007-03-07
P.S. - I checked the md5 sums for the ISO and the one provided by the mirror site, and they are identical.  That eliminates download errors.  I think there is a device support issue with my hardware.  Can anyone please  help?

---

