---
title: "[boot-repair] How to get back windows 8 uefi boot files"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by baletka on 2013-06-24
Hello,
I had working dual-boot with Windows 8 and Ubuntu (11.10 I think), then I upgraded ubuntu to 12.04 and 12.10 and ubuntu removed itself from efi boot options. So I ran boot repair, first time I used automatical repair and it didn't seem to do anything ([http://paste.ubuntu.com/5796475/](http://paste.ubuntu.com/5796475/)). Then I ran it again using advanced settings, but I think I didn't actually change anything that wasn't already checked, and ubuntu removed windows 8 boot files and replaced it with it's own, so now the "Windows" option in efi loads grub. I guess it does keep a copy, but I'm not sure which one is it, could anyone help me restore it? Pastebin: [http://paste.ubuntu.com/5796504/](http://paste.ubuntu.com/5796504/)

Also, I later upgraded ubuntu to 13.04 and it sucessfuly made it's own entry (so now I can load both Windows and ubuntu options to get into grub...), this is unrelated, but it might help as I noticed it's not only me that has ubuntu installed but no option in efi boot order.

---

### Post by baletka on 2013-06-24
I decided to just try it myself, and renaming /EFI/Microsoft/Boot/bkpbootmgfw.efi back to /EFI/Microsoft/Boot/bootmgfw.efi (as well as /EFI/Boot/bkpbootx64.efi to /EFI/Boot/bootx64.efi) solved it. When opening the thread I was concerned because I couldn't find a copy of /EFI/Microsoft/Boot/bootx64.efi, but it looks like it's not required. Does anyone know if that's just a copy of bootmgfw.efi?

---

### Post by oldfred on 2013-06-25
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

Boot-Repair has backups so you can undo it.

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 

Also:

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by ubfan1 on 2013-06-25
/EFI/Boot/bootx64.efi is the bootloader used for removable media (like a USB).  On a hard disk, the efi menu entries usually are for bootloaders in either /EFI/ubuntu or /EFI/Microsoft/Boot, but under some error conditions like an efi entry for a bad bootloader (grubx64.efi on a secure boot enabled for instance), there may be a silent fallback to try the bootx64.  At least that's the way Toshiba S855 works.  It's not a bad idea to make bootx64.efi a copy of shim, and also have a grubx64.eri in the same directory so the fallback is to grub.

---

