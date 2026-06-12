---
title: "Legacy Mode and UEFI"
date: 2015-08-06
forum: Installation &amp; Upgrades
---

### Post by permon on 2015-08-06
Hi I have installed ubuntu on my sony vaio in legacy mode alongside windows 10 but now when I try to go to windows with grub I get a windows bootloader error, I can boot xubuntu fine in legacy mode. If I turn boot mode back to UEFI in the bios setup I can boot windows, but then obviously I cannot see grub then. I had to install in legacy mode as my laptop did not allow me to boot from usb in uefi mode. Is there any way to fix booting into windows in legacy mode?

---

### Post by oldfred on 2015-08-06
UEFI and CSM/Legacy/BIOS mode are not compatible. Once you start booting in one mode you cannot switch to the other mode. Or once you start grub in Legacy mode you can only boot other installs in Legacy mode from grub. Or if booting grub in UEFI mode you an only boot other installs in UEFI mode.

You have to chose from UEFI boot menu or perhap one time boot key, often f10 or f12 with many systems.

You cannot convert Window to legacy mode. Or you can if you want to purchase a new copy of Windows and erase drive and convert drive to BIOS/MBR partitioning. Your pre-installed Windows has its key in the UEFI for UEFI installs.

You can convert Ubuntu to UEFI, with Boot-Repair but Sony makes it difficult to boot Ubuntu. It has modified UEFI to also use description and only valid description is "Windows".  That is not per UEFI standard.
But several work arounds are available and have worked on others with Sony systems.

Details in links in my signature or ask specific question and we can help.

---

### Post by permon on 2015-08-07
Thanks for the reply, I dont think I will bother to convert ubuntu to EFI and instead just switch between Legacy and UEFI mode when changing between OSs as it will keep the windows EFI partition isolated and separate :)

---

