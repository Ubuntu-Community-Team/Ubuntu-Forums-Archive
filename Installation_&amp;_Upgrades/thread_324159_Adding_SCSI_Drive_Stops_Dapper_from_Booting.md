---
title: "Adding SCSI Drive Stops Dapper from Booting"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by ScottCh on 2006-12-23
Hi Folks,

I have Ubuntu Dapper installed on my Athlon 64 desktop system on a single SATA hard drive.  The system also has an LSI Logic 53c895a SCSI host adapter.

I recently tried to plug a SCSI hard drive into the system, but when I did, it refused to boot.  There were no error messages.  The SCSI drive is terminated correctly, and has its own device ID.  The SCSI BIOS reports no problem.  But when the boot process reaches the point where the GRUB Boot Menu normally displays, the boot process hangs.

If I disconnect the SCSI drive, the system boots properly again.

I tried booting from my Ubuntu CD-ROM and selected "Rescue System" from the menu. I was able to start a shell from my disk0/partition 4 root partition. Using fdisk -l, I was able to determine that the disk assignments have not changed. The SATA hard disk is still /dev/sda, and the new SCSI hard disk is /dev/sdb. fdisk has no problem listing their partition tables.

I also checked the system BIOS settings. These allow the hard drive boot priority to be specified. The default boot priority settings seem correct. Boot priority #1 is the SATA drive, #2 is the SCSI drive, and #3 is "Bootable PCI devices". This looks reasonable to me.

Unfortunately, there is no way in the BIOSes to disallow the SCSI drive from being used as a boot device.

Someone in a different forum discussion mentioned that the system BIOS has its own device enumeration order, and that this affects GRUB at a more fundamental level than the device boot priority settings.  However, I have not been able to find a way around this problem - if there is one.

Does anyone have any wisdom, insight, etc. into this situation?

Much thanks!

--
Scott C in Cary, NC USA

---

