---
title: "boot repair - new to ubuntu"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by larry30 on 2015-03-28
After booting Win 8 grub will not boot. Ran boot repair once and it seemed to fix the problem, however, after booting widows again grub will not boot. Ran boot repair again and now the system will only boot from USB. No Win 8 boot option in the bios.

[http://paste.ubuntu.com/10698935](http://paste.ubuntu.com/10698935)

Any help would be greatly appreciated.

---

### Post by oldfred on 2015-03-29
Your UEFI is not showing a Windows entry??

from Boot-Repair's output of sudo efibootmgr -v

      ```
 BootOrder: 0003,0012,000D,000E,0000,0001,0002
Boot0000* P0: ST1000DM003-1CH162            BIOS(11,0,00)
Boot0001* KingstonDT 100 G2 PMAP    BIOS(12,0,00)
Boot0002* P1: TSSTcorp DVD+/-RW SH-216CB    BIOS(13,0,00)
Boot0003* ubuntu    HD(1,800,fa000,3147857e-e516-41b2-bbbd-de63e4d17089)File(EFIubuntushimx64.efi)
Boot000D* UEFI: IP4 Realtek PCIe GBE Family Controller (Ipv4)    ACPI(a0341d0,0)PCI(1c,5)PCI(0,0)MAC(74867afffbe7,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0AMBO
Boot000E* UEFI: IP6 Realtek PCIe GBE Family Controller (Ipv6)    ACPI(a0341d0,0)PCI(1c,5)PCI(0,0)MAC(74867afffbe7,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000AMBO
Boot0012* UEFI: KingstonDT 100 G2 PMAP    ACPI(a0341d0,0)PCI(1a,0)USB(1,0)USB(2,0)HD(1,1f80,1dca080,c3072e18)AMBO


```    

I thought Dell would directly boot ubuntu entry and also Windows entry.
Some systems will only boot Windows entry or a hard drive entry so we have to copy grub's files and rename them to either the hard drive bootx64.efi or Windows name. The rename of Windows file is not now suggested unless it is the absolute last resort.

Before making any more changes, make a full backup of the efi partition. Boot-repair may have copies on drive, but better to have your own copy on another device.

       New Windows entry:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

Not sure if Boot-Repair did any renaming of files, if so then bootmgfw.efi may not really be the Windows file anymore?

Other work arounds in link in my signature and this:
      
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

