---
title: "Ubuntu 12.04 dual-boot problem with windows 8"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by enrico-massa on 2013-08-13
Hi,

I'm trying to boot Ubuntu from my fresh installation on a HP Envy dv7 along side windows 8. I have followed the standard instruction for installation, I have disabled Secure Boot from Bios, and I have repaired the boot sector using boot repair as show here:
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Here is the result given by boot repair, with no error:
[http://paste.ubuntu.com/5982404/](http://paste.ubuntu.com/5982404/)
Unfortunately when I reboot the machine I just get the standard windows 8 and no boot loader is shown. 
Any help would be really appreciated. Thanks.

---

### Post by oldfred on 2013-08-13
Have you gone back into UEFI and selected ubuntu to boot. The default was Windows and is not automatically changed.

---

### Post by enrico-massa on 2013-08-13
Thanks oldfred. I missed that bit. I writing you from Ubuntu now!

---

### Post by oldfred on 2013-08-13
Glad that worked. :)

HP's have a lot of efi files in its efi partition, so Boot-Repair makes a lot of entries into 25_custom. You may want to houseclean but have to do it manually. More info in link in my signature.

---

### Post by enrico-massa on 2013-08-13
Thanks again oldfred. Actually another problem is that after reboot windows is still default in UEFI and I have to restart in troubleshoot mode each time. Is there any solution to that?

---

### Post by oldfred on 2013-08-13
Is that from fastboot or perhaps some other setting? I thing the repair mode in Windows resets it to be the default, but why is it not just booting. Most do, but a few are reporting issues. Not sure what Windows setting that may be. I do not have nor expect to ever have Windows 8.

---

### Post by enrico-massa on 2013-08-14
Fastboot is off. This is the output of efibootmgr:
BootCurrent: 0002
Timeout: 4 seconds
BootOrder: 3001,3002,2001,2002,2003
Boot0001* Windows Boot Manager
Boot0002* Ubuntu
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
I'm not sure why Ubuntu doens't appear in the boot order. Should I just chance the order putting Ubuntu first?

---

### Post by oldfred on 2013-08-14
Another HP Envy user posted that he had to turn secure boot off, Legacy boot on and it booted in UEFI mode after UEFI was configured. It seems the system looks for UEFI (without secure boot) or efi partition with boot files first and then if not found will boot in BIOS mode from MBR, all automatically. Makes it a bit more difficult to really know which way it is really booting.

You seem to have 3001 as default which just specifies a drive, But you have 00002 as Ubuntu. But I do not know then if that is UEFI or not? I would think that would be UEFI entry as that is more how UEFI's show boot entries and BIOS normally just show drives as it cannot query MBR to know what is in MBR. UEFI queries efi partition to know each folder for booting.

---

