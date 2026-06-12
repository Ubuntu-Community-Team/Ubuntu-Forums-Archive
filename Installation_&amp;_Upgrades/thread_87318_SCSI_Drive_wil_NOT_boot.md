---
title: "SCSI Drive wil NOT boot"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by balagula on 2005-11-07
After what seems to be a normal installation, the system will not boot. "Disk boot failure" message is displayed. 
This is X86 system equipped with Adaptec 2940U and one 18 GB SCSI drive. Drive is set to "0" SCSI address. 
Any ideas?

---

### Post by metoo on 2005-11-08
Stupid question, but this sounds more like a BIOS message:
Everything OK in this area? No floppy/usb stick/CD in any drive? System booted fine over the SCSI HD previously? Grub installed without errors and boot partition flagged as bootable?

---

### Post by x__dark on 2005-11-08
If GRUB won't show up then you might have a problem with your MBR. If you do, you might as well reinstall Ubuntu and see if it'll work afterwards. Are you dual booting with anything? I have had problems with GRUB and dual booting my SCSI drive.

---

