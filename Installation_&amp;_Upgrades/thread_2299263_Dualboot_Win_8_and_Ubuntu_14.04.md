---
title: "Dualboot Win 8 and Ubuntu 14.04"
date: 2015-10-16
forum: Installation &amp; Upgrades
---

### Post by Elizaveta_Kishchuk on 2015-10-16
[http://paste.ubuntu.com/12812395/](http://paste.ubuntu.com/12812395/)

I can't load to Windows 8, when I returned to UEFI mode from legacy mode. Windows Boot manager disappeared from boot menu, and when trying to boot, I've got the mesages "No bootable device"

Boot Repair was completed successfully, but I still can't load to Windows, and only can upload to Ubuntu from legacy mode

Laptop Asus Aspire v13

---

### Post by oldfred on 2015-10-16
You show no NTFS partitions. Your Ubuntu is installed in BIOS mode with MBR partitions. So without NTFS partition and with MBR(msdos) partitions there is no way you have any Windows install.

Did you make good backups before installing? Or at least the vendor image of hard drive as purchased and all your data? My new Dell insisted I make both Windows & Dell backups when I first booted Windows.

With UEFI you want to always install additional operating systems in UEFI also.

While you cannot restore a bootable system, it you had data you want to attempt to recover, you may be able to use testdisk or photorec.  But STOP using system as everything you are doing is overwriting more of your old data. Only use live installer.

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

