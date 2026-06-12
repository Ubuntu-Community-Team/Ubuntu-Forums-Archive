---
title: "SCSI CD-Rom detection issues"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by zencoder on 2005-10-19
I am having difficulty getting the installer to recognize the SCSI CD-Rom as the source for packages.  System boots normally and I can enter the installer program, but when it looks for the local CD-Rom to install initial packages, it can't find it (despite having booted from this device already.)

Relevant specs:
SuperMicro P6DBS (yes, ancient)
AIC7895 SCSI Controller (onboard, built into the Mobo)
Toshiba SCSI CD-Rom

I've tried booting with aic7xxx=no_reset and scsi=cdrom, but with no luck.  Any ideas?  Or is there a listing of ALL parameters that can be passed to the boot media?

---

