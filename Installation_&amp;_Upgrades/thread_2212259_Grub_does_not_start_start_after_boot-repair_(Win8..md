---
title: "Grub does not start start after boot-repair (Win8.1 /EFI)"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by matt.vt.beck on 2014-03-20
I installed Ubuntu 12.04.04 alongside Windows 8, following the steps indicated in these links:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

My problem is now that even after the boot-repair (from my LiveUSB) Grub does not appear, instead Windows 8 is always booting.
This is the URL from the boot-repair report: paste.ubuntu.com/7124765/

I have a Sony Vaio Notebook (SSD) with UEFI.
These are the steps I did:
1. Created the Live USB (64bit)
2. disabled FastStartup
3. Installed Ubuntu (no secure boot error, so I kept it enabled) in UEFI mode
(Here Ubuntu automatically choose my data partition where Windows is not installed, maybe the problem lies here?)
4. Reboot... now Windows 8 started, not Grub
5. Boot-repair as described here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

6. Reboot... again Windows started
7. Boot-repair again, this time with SecureBoot disabled, reboot... same result

---

