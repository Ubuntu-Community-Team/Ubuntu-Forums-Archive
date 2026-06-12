---
title: "Can't boot from CD (SMP problem?)"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by Impute on 2008-01-27
I've been having a few problems getting 7.10 to boot, even from CD.

The graphical 7.10 CD just stops and reboots part way through the installation.

If I remove the "quiet" from the boot options I see that it reboots just after writing:
  "booting processor 1/2"

If I remove the "quiet" and add "nosmp" to the boot options I make it up to 
  "ACPI: PCI interupt disable for device 000:03:00.1"
  "pata_jmicrom probe of 000:03:00.1 failed with error -38"
then it gets stuck repeatedly writing:
  "end_request: I/O error dev fdo sector 0"

If I use the alternate text only 7.10 CD, remove the "quiet" and add "nosmp" to boot options I get up to the language selection screen. However the keyboard doesn't work, so I can't go any further.

Any suggestions as to what I should try next? (Short of uninstalling Windows or removing the RAIDing, which I'm not willing to do.)


Hardware:
  Intel Core2 Duo
  Gigabyte GA-P35-DS3R motherboard
  Nvidia 8800GT graphics card
  Windows XP is installed on 2 mirrored drives (Western Digital 500GB SATA 2) using the motherboard's RAID 1
  I'm trying to install Ubuntu on a separate single drive (Segate 250GB SATA 2)
  DVD-RW (Pioneer SATA) 
  Logitec USB mouse and keyboard
  I'm using the Intel ICH9R SATA controller for all the drives

Thanks.

---

### Post by Impute on 2008-02-11
The latest alpha (8.04) appears to fix this problem. It takes a while, but after producing errors for a few minutes it eventually gives up on fd0 and boots correctly, so I suppose this is resolved.

I've since discovered that the installer does not play nicely with Windows RAID -- by default (and without telling you unless you look in the right part of the advanced settings)  it installs a boot loader to the first hard drive it finds, even if that drive is one half a RAID pair. This corrupts the Windows RAID array.

---

### Post by evident on 2008-02-23
i have the exact same config as you almost.  i can't seem to install ubuntu either and can't even get to the live CD, it just hangs after it says that i am in low graphics mode, and even if i click on configuration and choose, it hangs afterwards.  i've given up for now on ubuntu.... fedora 8 seems to install just fine though,

---

