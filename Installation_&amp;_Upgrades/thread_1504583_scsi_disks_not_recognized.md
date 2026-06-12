---
title: "scsi disks not recognized"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by ororo on 2010-06-08
Dear all,
I am trying to install Ubuntu Lucid Lynx on a 64-bit pc. I want to use it as both a desktop and a server, so I decided to install the "Desktop" AMD64 edition.

But, when I run the installer, my hard disk (SCSI) is not recognized.

I think the problem is that the SCSI modules are not loaded at startup. Indeed:

(1) Previously, I had Hardy on that server, and it always loaded the "scsi_mod" module. Actually, I cannot find such a module on the Lucid Lynx Live CD.

(2) There are many other scsi-related modules in the Live CD. I have manually loaded some of them (e.g. "sudo modprobe st") and /sometimes/ my HD appears. But, when I run the installer, it "umount"-s the disk, and it tell me that there are no disks present on my machine.

Do you know what module should I load? or what should I do?
Thank you!

EDIT
Sorry, there were some errors in my post.

(1) I don't know if the disk is SCSI or SATA. Both BIOS and lshw say SATA, but the disk is in /proc/scsi/scsi, too.

(2) The disk is RAID: two different 500Gb disks, one the backup-copy of the other one, considered as a single 500Gb disk.

(3) The disk IS recognized by the Live CD, with no need of modules. It appears in the "Places" Gnome menu. Nevertheless, the installer cannot see it, and tells me there are no disks on my system.

---

