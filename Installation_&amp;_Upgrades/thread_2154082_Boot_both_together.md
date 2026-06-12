---
title: "Boot both together"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by Andrew Bastin on 2013-06-13
Hello there,

I installed ubuntu 13.04 on my PC with efi and booted to grub. Then I noticed that windows could not boot so i changed UEFI firmware settings to boot to Windows and I have to toogle the first bloot device if I have to boot to ubuntu then switch back to windows.tried out EasyBCD and messed up the windows 8 bootloader.it shows all devices like usb cd, network and one option called ubuntu. I clicked it and came up with a boot error.

Is there a way to unite the bootloaders together?

Andrew Bastin

---

### Post by darkomano on 2013-06-13
Do not use EasyBCD as it is not UEFI capable - it cannot create loaders for UEFI/GPT. First of all you should repair Windows booting using Windows installation or recovery media (which should be booted UEFI way). Then use [BootRepair]("https://help.ubuntu.com/community/Boot-Repair") to repair Ubuntu booting. Ubuntu/Grub can boot both - Ubuntu and Windows (by chaining).

---

### Post by oldfred on 2013-06-13
Did you install Ubuntu in BIOS/Legacy/CSM mode not UEFI. Both have to be installed in UEFI mode to easily dual boot. Boot-Repair can fix that by uninstalling grub-pc(BIOS) and installing grub-efi(UEFI).
Then as darkomano says above you can chain load from grub2 to Windows.

---

### Post by Andrew Bastin on 2013-06-14
I installed both the OS on UEFI mode.
And I installed Windows 8 Pro but the PC came with Windows 8 SL 64-bit
And I installed Ubuntu on divided Windows 8 partition.

Let me try the way darkomano  but I kept Windows 8 Pro disk with my other disks.
And I am lazy to download boot-repair.

Andrew Bastin

---

