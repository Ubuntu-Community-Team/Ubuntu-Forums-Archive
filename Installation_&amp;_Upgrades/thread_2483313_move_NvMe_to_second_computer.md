---
title: "move NvMe to second computer"
date: 2023-01-26
forum: Installation &amp; Upgrades
---

### Post by jloveless on 2023-01-26
I have a 2TB NvMe with the latest Ubuntu (23.10) as well as current UbuntuStudio and Zorin in a dual (triple) boot. I have purchased a second PC. Similar to this one. I want to switch the SSD drive with OSes from old to new. Should I expect the new one to boot from the original SSD? If not can someone guide me with steps to get it to boot? Many thanks.
Jon

---

### Post by Frogs Hair on 2023-01-26
Did your new computer include an operating system and if so, are you planing to leave it on the new system? You may have respond to new hardware prompt during boot and select a boot device in the bios.

---

### Post by Impavidus on 2023-01-26
You must be from the future. Ubuntu 23.10 will only start development 3 months from now.

In general, you can move a harddrive with Linux from one computer to another and simply expect it to boot. Just keep in mind:
- Both must be UEFI or both must be legacy mode. Legacy mode is getting a bit uncommon these days, so I don't expect that will be a problem.
- Both must use the same architecture (although 32 bit in an amd64 computer works). Pretty much all computers are amd64 these days, except the ARM systems.
- Before moving, disable proprietary graphics drivers, if any, unless both computers use the same graphics hardware.

---

### Post by tea for one on 2023-01-26
Remove, isolate or de-activate the drive from your new PC to avoid any potential boot conflict.
Insert your triple boot drive and...........success?

---

### Post by oldfred on 2023-01-26
A grub install adds an "ubuntu" entry to UEFI to boot /EFI/ubuntu/ or maybe /EFI/grub if one of the other installs in ESP - efi system partition. You will not have that UEFI boot entry.

You should be able to boot a fallback or drive boot entry that uses /EFI/Boot/bootx64.efi. Grub normally creates that now for internal drives. This also is how all external drives boot.

You can reinstall grub once booted or use efibootmgr to create new UEFI boot entry.

---

