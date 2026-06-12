---
title: "Dual booting on HP Omen overwrites bootmgfw.efi"
date: 2017-10-05
forum: Installation &amp; Upgrades
---

### Post by duncan1a on 2017-10-05
I'm trying to dual boot my new HP Omen 15.

At first windows 10 kept overwriting the grub so that it booted only into windows.

Then I followed some instructions - can't recall exactly what, but it involved moving EFI/Microsoft/Boot/bootmgfw.efi to EFI/Microsoft/bootmgfw.efi

Now I get grub, but when selecting windows it said that EFI/Microsoft/Boot/bootmgfw.efi didn't exist.

I copied EFI/Microsoft/bootmgfw.efi to EFI/Microsoft/Boot/bootmgfw.efi. That works.

Now after some reboots EFI/Microsoft/Boot/bootmgfw.efi is zero bytes and I have to copy it agin form ubuntu to be able to boot windows.

I'm sure if windows or Ubuntu is zeroing out EFI/Microsoft/Boot/bootmgfw.efi.

How do I get grub to boot windows without having to keep copying this file all the time?

---

### Post by duncan1a on 2017-10-06
I seems to be Ubuntu doing the overwriting. If I reboot to windows it's fine. As soon as I boot into ubuntu then EFI/Microsoft/Boot/bootmgfw.efi is overwritten

---

### Post by oldfred on 2017-10-06
That is the standard Windows boot file at EFI/Microsoft/Boot/bootmgfw.efi, Ubuntu would not be overwriting that and normally only on grub install or update would write into /EFI/ubuntu in same ESP - efi system partition.

Some HP directly boot the fallback/hard drive entry at /EFI/Boot/bootx64.efi, which is just a copy of the bootmgfw.efi file. And for most HP we have to copy /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi to boot Ubuntu using hard drive entry, not ubuntu entry in UEFI.

Be sure to boot in UEFI mode.
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

