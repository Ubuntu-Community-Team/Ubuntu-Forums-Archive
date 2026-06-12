---
title: "Recognising IDE disks after SCSI server install"
date: 2005-07-03
forum: Installation &amp; Upgrades
---

### Post by wookie on 2005-07-03
I'm installing to an old NCR server which came to me with SCSI disks.  It appears that the BIOS of this machine is only able to recognise SCSI disks even if I add a 200gig ATA drive on a PCI Silicon Image controller.

Doing standard installs I found that 5.03 would install onto the SCSI disks OK, but if I had the ATA disk present when grub was installed, the installer would wrongly assume that I could and wanted to boot off the ATA drive, and would configure GRUB accordingly, even though the BIOS would not be able to find the drive.

I have worked around this by leaving out the ATA drive during the first part of the install.

I did a standard install of 5.03, the first part to SCSI disks only.  On rebooting with the ATA drive added, I was able to set it up, configure reiserfs, write files to it etc.

As I failed to be able to configure X during the standard install, I decided to redo the installation as 'server' at the CD boot prompt, but having now done a server install (again leaving the ATA disk out for the first part), I now find that when I reconnect it, not only is it unrecognised, but /dev/hda* aren't in the file system !

What do I need to be able to do to access my ATA drive ?

Is there a guide to building functionality on top of the 'server' install ?


Many thanks, J/.

---

