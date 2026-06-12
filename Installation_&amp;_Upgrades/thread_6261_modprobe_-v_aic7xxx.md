---
title: "modprobe -v aic7xxx"
date: 2004-11-26
forum: Installation &amp; Upgrades
---

### Post by prescor on 2004-11-26
I'm trying to install Ubuntu on my G4 Mac. I have an Adaptec SCSI card with a 9GB drive attached to it. I want this drive to be my boot volume.

I get the installer to run, but when it attempts to detect CD-Rom drives, I get an error:

"Error while running 'modprobe -v aic7xxx'"

I have an option to continue, but when I do, this part of he installer hangs at 16%.

If I remove the SCSI card, everything is fine.

I should note that this card had previously worked with Yellow Dog Linux. Is there any way I can modify the installer, or tell it not to look to SCSI cards for CD-ROM drives?

Thanks,
...ROMeyn

---

