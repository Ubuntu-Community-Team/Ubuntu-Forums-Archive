---
title: "Gutsy (64) on ThinkPad X61 w/250GB HD"
date: 2007-10-06
forum: Installation &amp; Upgrades
---

### Post by mfbernstein on 2007-10-06
I've installed several betas of Gutsy (amd64) on my Thinkpad X61. After upgrading to a Western Digital Scorpio 250GB HD, I attempted to install using the same CD as before.

Install appears to go fine, but upon reboot, GRUB gives an "unknown partition" error. Apparently root was set to the wrong partitition in grub.conf (hd0,0) instead of (hd0,1). After correcting this, the bootup process will begin, but hangs right after loading the USB HID drivers (in rescue mode).

Other operating systems on this disk (Windows XP, memtest86) work fine.

Any ideas what be going wrong, or how to figure out the problem? I'm puzzled because an install last week on a similarly partition 200GB Toshiba HD in the exact same machine worked without any problems.

Thanks.


(System config: ThinkPad X61 w/250GB WD Scorpio 5400RPM SATA HD, UltraBase X6 with CDRW drive, SATA is set to "Compatibility" mode in the BIOS)

---

