---
title: "Alternative and Minimal image issues on EeePC 1101HA"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by Jimage on 2010-08-16
The minimal and alternative installers are not conductive to my EeePC 1101HA:

Alternative chokes when trying to detect a CD-ROM drive (USB drive or SD card boot are the only options). I tried mounting a copy of the ISO directly to /dev/sr0, which kind of worked, but it wouldn't let me enter a manual path to the CD device when the second CD-ROM scan came up.

Minimal doesn't have the atl1c ethernet module, nor the module required for the wireless chipset, and I cannot mount any storage devices ("mount: mounting /dev/sda1 on /mnt/usb failed: Invalid argument").

The 9.10 live CD encounters no problems, and I can install perfectly from there, but I wish to start with a pure command line system this time and build the rest up from there.

What can I do to:

a) make the installer accept a mounted ISO all the way through, or

b) add the atl1c module to the minimal boot image in order to modprobe it?

Cheers.

---

