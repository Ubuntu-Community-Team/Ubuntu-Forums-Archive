---
title: "Grub rescue opening after updating Ubuntu 16.04 to Ubuntu 18.04"
date: 2018-06-01
forum: Installation &amp; Upgrades
---

### Post by shaadali111 on 2018-06-01
Hello,
      I updated my hp machine to Ubuntu 18.04 after using dual boot ubuntu 16.04 and win 8.1 for quite some time.
     Now every time I boot, the following error pops up:
"error: unknown filesystem.
Entering rescue mode...
grub rescue> "
     I tried to find the ubuntu partition and the grub modules but the modules were not present at (hd2,msdos7)/boot/grub or (hd2,msdos7)/usr/lib/grub/i386-pc

     I tried booting ubuntu 18.04 with usb and running boot-repair but it throws the error:
"grub-install: error: cannot find EFI directory.
dpkg: error processing package shim-signed(--configure):
  installed shim-signed package post installation script subprocess returned error exit status 1"

     I aso tried reinstalling ubuntu 18.04, erase Ubuntu 18.04 and reinstall and it stops while installing grub2 package. I posted this error before on launchpad.net but there was no reply. Here's the link of the thread: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1774357](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1774357)

     Here is the boot-repair summary if anyone need:
[http://paste.ubuntu.com/p/S9R3bYK885/](http://paste.ubuntu.com/p/S9R3bYK885/)

     I found some pages where it was discussed that bios can only read 137GB memory and if the grub files are beyond that limit this results in this error. Link: 
[https://ubuntuforums.org/archive/index.php/t-1760590.html](https://ubuntuforums.org/archive/index.php/t-1760590.html)

Please look into it and thanks in advance.

---

### Post by oldfred on 2018-06-01
Are drives set for AHCI, not RAID, IDE, not some Intel SRT or similar setting.
The beyond 137GB boot issue was for now very old BIOS systems. Some newer systems with IDE setting my emulate that error and some USB boot drives. 
Have yet to see that as an issue on any newer UEFI capable system.

Since your installs are BIOS boot on MBR(msdos) partitioned drive, do not boot Ubuntu live installer in UEFI mode.
Reboot Ubuntu live installer in BIOS mode from UEFI boot menu and rerun report and see if you can reinstall grub-pc (BIOS version).

---

