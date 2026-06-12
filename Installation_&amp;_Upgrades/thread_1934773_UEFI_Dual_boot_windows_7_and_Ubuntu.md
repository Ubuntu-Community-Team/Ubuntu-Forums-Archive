---
title: "UEFI Dual boot windows 7 and Ubuntu"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by bohregard on 2012-03-02
Ok so I'm having a bit of trouble.

I have installed Ubuntu on my hard drive first and then partitioned and installed Windows 7. The problem I'm having is that I can't get grub to recognize the Windows 7 partition, but I can boot into Windows from my bios.

My setup is
/dev/sda1/ efi partition
/dev/sda2/ linux
/dev/sda3/ swap
/dev/sda4/ windows boot thing
/dev/sda5/ windows 7

I've run update-grub to no avail, and I've also tried booting into grub and running

```
set root=(hd0,4)
chainloader +1
boot
```
and
```
set root=(hd0,5)
chainloader +1
boot
```

But both times it says invalid EFI partition. I know that the windows 7 partition is an EFI partition, but I'm at a loss! Any help is greatly appreciated.

---

### Post by mjg59 on 2012-03-03
You can't just chain a partition in EFI. First, make sure that you're using an EFI build of grub - you can't enter BIOS compatibility and then jump back to EFI. Then it should just be a matter of:

set root (hd0,gpt1)
chainloader EFI/microsoft/bootmgr.efi

or whatever the path to the Microsoft EFI bootloader is.

---

### Post by oldfred on 2012-03-03
I have in my notes these choices, but do not have UEFI.

[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

[https://wiki.archlinux.org/index.php/UEFI#UEFI_Shell](https://wiki.archlinux.org/index.php/UEFI#UEFI_Shell)
boot to efi shell:
cd fs0:
cd efi\Microsoft\Boot
bootmgfw.efi

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

---

### Post by bohregard on 2012-03-04
Ok, I fixed the problem.

In my 40_custom I added a new entry

```
menuentry "Windows 7 UEFI" {
  insmod part_gpt
  insmod fat
  insmod search_fs_uuid
  insmod chain
  set root='(hd0,gpt2)'
  search --fs-uuid --no-floppy --set=root 4f84-ee2e
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}
```

This fixed the problem completely.

Thanks for the help everyone.

---

