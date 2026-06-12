---
title: "boot repair - dual boot, ubuntu boot fails after upgrade to 22.04.3"
date: 2023-12-22
forum: Installation &amp; Upgrades
---

### Post by panibillo on 2023-12-22
Dear community,  I'm having trouble with boot into ubuntu after upgrading from 20.04(?) to 22.04.3 (20.0-something anyway). Seems to do with mixup between Legacy bios and uefi.  The system was very stable before upgrade attempted. I've tried the recommended repair with boot-repair, but still get the error messages:
   [FAILED] Failed to mount etc/fstab
   [DEPEND] Dependency failed for Local File Systems

The boot-repair summary, after running the recommended repair, is posted to   [FONT=&amp]https://paste.ubuntu.com/p/JjZWTyx7gv/
[/FONT]
Boot into Windows 10 still works, but goes through 2 choice screens: First has 4 choices (2 ubuntu & 2 Windows). The second has 2 choices (1 ubuntu 20.04 & 1 Windows).  Both menus are ASCII-like. The Windows boot works.  Windows reports that it is using Legacy bios.

I'm a little overwhelmed with the number of choices to make.  Appears that it might be possible to alter Windows from Legacy boot to uefi, but I don't know what grub is trying to do.  Maybe easier to create a new efi partition, and then try boot repair again.  Any advice will be most welcome.
Thanks!

---

### Post by oldfred on 2023-12-22
You cannot easily convert Windows from BIOS to UEFI. Issue is primarily that BIOS Windows requires MBR and UEFI Windows requires gpt.
And conversion from MBR(msdos) to gpt totally erases drive.
Microsoft did have a tool to convert, but some that have tried it, posted they just ended up reinstalling.
Conversion works best on data only drives, not drives used for booting.

You also cannot mix UEFI & BIOS on same drive.
Windows requires a boot flag on its boot partition, and UEFI requires boot,esp flags on ESP - efi system partition. Only only one active boot flag per drive for most systems.

Microsoft has required UEFI/gpt since release of Windows 8 in 2012, so most hardware is now UEFI capable.

Grub only boots working Windows. That also means Windows cannot be hibernated, nor fast start up on which also sets hibernation flag.
If newer Windows bitlocker must also be off. Even if you turned fast start up off, Windows updates may turn it back on. And Windows update may include an UEFI update which often resets the settings you had to change to install Ubuntu back to defaults. 

With BIOS and one drive, you only have one MBR to hold boot info. So you have to have grub installed to MBR.
But if issues with Windows you then have to temporarily install a Windows boot loader to MBR to boot Windows, make repairs, then reinstall grub to MBR.
Always have both Ubuntu live installer for current installed version and Windows repair/recovery flash drive so you can do the boot loader dance.
With UEFI you should always be able to directly boot either install directly from UEFI boot menu. So if Windows issue, you just boot it, no reinstall of boot loaders required.

Long term, best to have really good backups and convert to UEFI/gpt for both installs. But unless new larger/faster drive or other major change, hassle of conversion probably not worth it.

---

