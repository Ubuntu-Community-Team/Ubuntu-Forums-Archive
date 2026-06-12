---
title: "unable to boot into windows after failed ubuntu install"
date: 2022-12-07
forum: Installation &amp; Upgrades
---

### Post by jheronimus-fnord on 2022-12-07
Hello all.

I got in way over my head today trying to install ubuntu alongside my win10 installation (same drive), on thinkpad x270.
There is no GRUB menu and the machine boot loops regardless of boot priority settings. It does not seem to find any bootable OS.


Boot repair windows boot files is greyed out. I see the windows partition in Gparted.

I probably got confused somewhere with EUFI/BIOS and MBR/GPT settings. I attempted to install Ubuntu from USB but got a critial GRUB error.

here is the log:

[https://paste.ubuntu.com/p/BFkQqfs2Rq/](https://paste.ubuntu.com/p/BFkQqfs2Rq/)

Can someone offer assistance? Thanks so much in advance.

---

### Post by ubfan1 on 2022-12-07
Looks like your Windows install is legacy (msdos partitioning), but your Ubuntu install was in UEFI mode.  Your Lenovo (probably) has UEFI (aka BIOS) settings for boot mode, allowing both, but with a preference.  Since the Ubuntu install media boots both ways, it booted in UEFI mode, and installed in UEFI mode, creating an EFI partition.  Change the boot mode to legacy first to get back to windows.  Either reinstall Ubuntu (something else and clean up the old Ubuntu install) or more difficult, just reinstall grub-pc and clean up leftover UEFI stuff like /boot/efi,  & fstab entries.

---

### Post by tea for one on 2022-12-07
[COLOR="#0000FF"]Line 5[/COLOR] - Windows 7/8/10/11/2012 is installed in the MBR of /dev/nvme0n1
This means that you have Windows in Legacy mode.
[COLOR="#0000FF"]Line 18[/COLOR] - File system:       BitLocker
Is Bit Locker enabled?
[COLOR="#0000FF"]Line 44[/COLOR] - File system:       vfat (nvme0n1p7)
It appears that you tried to install Ubuntu in UEFI mode.

On one disk, you have to have both systems installed in the same mode i.e. Legacy or preferably UEFI.
Info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you have backups of your Windows data?

---

### Post by oldfred on 2022-12-07
You show a Windows UEFI boot entry??
Did system originally come with Windows and you reinstalled in old BIOS/MBR boot mode?
Microsoft requried vendors to install in UEFI boot mode to gpt partiitoned drives starting in 2012.

You also need to move boot flag back to nvme0n1p1, the Windows boot partition.
UEFI install has boot, esp flags on ESP -efi system partition. You can only have one boot flag per drive and Windows in BIOS mode must have boot flag on its boot partition.

---

