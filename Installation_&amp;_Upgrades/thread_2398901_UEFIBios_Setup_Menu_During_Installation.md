---
title: "UEFI/Bios Setup Menu During Installation"
date: 2018-08-19
forum: Installation &amp; Upgrades
---

### Post by thumbult on 2018-08-19
I just thought it would be good to include a setup menu during installation that would allow the user to choose between booting with UEFI or BIOS and the default should be UEFI which would allow maximum convenience and security but the option to boot with BIOS legacy could allow a user with multiple system drives to boot across devices.

---

### Post by oldfred on 2018-08-19
Not easily done.

UEFI and BIOS are not compatible. 
Once you start booting in one mode, you cannot switch. And systems may need UEFI settings to enable one mode or another mode.  So user has to go into UEFI to allow BIOS boot.

And user has that choice when booting from UEFI boot menu. It show UEFI or BIOS boot options for flash drive, but only if UEFI settings have been changed to allow BIOS boot.

UEFI and BIOS write hardware data for operating system onto hard drive differently. 
Some boot managers do a UEFI one time reboot to reset system and boot in other mode.

I believe Intel has suggested to manufacturers to use class 3 UEFI in the 2020 time frame. Class 3 has no CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mod.

---

