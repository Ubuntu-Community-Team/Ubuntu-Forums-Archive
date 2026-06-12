---
title: "GRUB on wrong Disk"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by saransk on 2007-06-29
I have been trying to resolve a weird installation problem. Here's the configuration:
@80Gig SCSI (Fast/wide) drive on Adaptec 2940 controller as boot 
IDE 40Gig removable drive for Data, & Backups on Primary IDE channel.  (Drive is in caddy)
With the IDE drive installed and turned on - Run Ubuntu installer, partition and install on SCSI drive [sda(0,0,0)].  GRUB appears to be installing on the IDE drive.
When I reboot, the startup either hangs or I get a "Bad PBR' message.  If I boot off of the DVD, the SCSI drive appears to be set up correctly in the partition manager.
If I disable the IDE drive, installation is fine, but then the IDE drive won't mountwhen I put it back in and restart the system.

Not sure what I'm doing, I'm sure it is a simple fix.
Thanks
Saransk

---

### Post by logos34 on 2007-06-29
> If I disable the IDE drive, installation is fine, but then the IDE drive won't mountwhen I put it back in and restart the system.

If you install linux with the ide drive disabled, then it won't be detected by the installer and added to fstab.  Thus it won't automatically mount when you reboot.  You'll have to add entry to /etc/fstab.

> With the IDE drive installed and turned on - Run Ubuntu installer, partition and install on SCSI drive [sda(0,0,0)]. GRUB appears to be installing on the IDE drive.
When I reboot, the startup either hangs or I get a "Bad PBR' message. If I boot off of the DVD, the SCSI drive appears to be set up correctly in the partition manager.

Either the ubuntu root partition is not active, or you're booting to the scsi drive when grub is on the IDE drive.  (Grub defaults to the MBR of the first detected IDE Bios drive).  If you are definitely booting to the IDE drive when you get that message, boot up the ubuntu live cd and type:
[B]
sudo fdisk -l [/B]

There should be an asterisk (*) next to your linux root partition.  If there is none, open Gparted/Gnome Partition Editor, right-click on the root partition and select '**manage flags**'. Tick the 'boot' box.

[COLOR="Blue"]ADD:[/COLOR] Look, if you can boot fine to ubuntu when you install with the IDE drive disconnected, just leave it like that (grub on the scsi MBR) and add an entry for the partition(s) on the IDE to your fstab file.  What filesystem is it formatted as?  I can give you some lines to insert so it will mount.

---

