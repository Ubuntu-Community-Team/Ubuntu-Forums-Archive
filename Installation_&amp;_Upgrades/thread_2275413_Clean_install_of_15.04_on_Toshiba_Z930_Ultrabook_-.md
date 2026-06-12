---
title: "Clean install of 15.04 on Toshiba Z930 Ultrabook - UEFI issues"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by leogaggl on 2015-04-25
I have been installing a clean new install of 15.04 on a Toshiba Z930 Ultrabook which previously has worked fine with 14.04 as the single OS. For whatever reason boot-repair does not fix the issue and I have tried several boot modes & fixes (including reFind).

Here is the boot-info output: [http://paste.ubuntu.com/10893357/](http://paste.ubuntu.com/10893357/) 

Any pointers greatly appreciated !

---

### Post by leogaggl on 2015-04-26
The base issue is that GRUB does not load at all. With 'Secure Boot' disabled I get: 

Booting in insecure mode.
Failed to open \EFI\BOOT\grubx64.efi

With 'Secure Boot' enabled GRUB failes to load and it moves to PXE boot ...

---

### Post by ubfan1 on 2015-04-26
Since the file \EFI\BOOT\grubx64.efi does not exist (according to your paste), of course it will fail open, but what's trying to open it?  Your item 4 in nvram is for /EFI/ubuntu/shimx64.efi, which should work to boot the /EFI/ubuntu/grubx64.efi with either secure boot enabled or disabled.  Just to confuse things further, you have additional bootloaders refind and a partial grub legacy in the master boot block.  Take a look at the size of /EFI/BOOT/bootx64.efi (mounted at /boot/efi if running Ubuntu on the hard disk, or mount it yourself if running live media) to try and determine what bootloader it really is, either Microsoft's bootmgfw.efi, shimx64.efi, grubx64.efi, or refind_x64.efi.  I don't know about refind, but if the bootx64.efi is a copy of shimx64.efi, and a copy of grubx64.efi is present in that directory, it should boot in either secure or non-secure mode, pulling in the /EFI/ubuntu/grub.cfg file.  This grub.cfg file is a very short file which should just pull in the maintained grub.cfg file from /boot/grub/grub.cfg.
  Since what you posted looks like it should successfully boot ubuntu, maybe the legacy grub boot block is confusing things -- some machines might default to that when both choices are present.

---

### Post by leogaggl on 2015-04-30
Thanks for your assistance ! I ended up switching back to CSM (Legacy boot). This whole UEFI is one of the biggest wastes of time and quite frustrating to debug. The boot-repair seems to introduce as much problems (adding Windows boot files even when there is no Windows installed on the system as well as the refind EFI files).

Thanks for your help again ! For those wanting to install 15.04 on the Z930 Toshy's save yourself some trouble and disable 'secure boot' and switch to CSM boot rather than UEFI boot in the advanced BIOS options.

---

