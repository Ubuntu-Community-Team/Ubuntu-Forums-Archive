---
title: "Super Grub2 On USB"
date: 2014-06-05
forum: Installation &amp; Upgrades
---

### Post by d.riess on 2014-06-05
Could someone please tell me how to put Super Grub2 on to a bootable USB.

I use Rufus to create all my bootable media but when I select the *super_grub2_disk_x86_64_efi_2.00s2.iso* I get this error,

[I]'Unsupported ISO
This version of Rufus only supports bootable ISO's based on bootmgr/WinPE, isolinus or EFI.
This ISO doesn't appear to use either.'
[/I]
It's recommended to use Yumi for SG2 but that only does MBR and my system is GPT & UEFI only (wouldn't boot).

I also used Rufus to create a Ubuntu Live USB and that worked so I don't know whats different about SG2.

Appreciate the help, thank you.

---

### Post by oldfred on 2014-06-06
It looks like it uses an efi.img file.

USB-Creator was fixed to allow use of a efi.img file several years ago.
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/677260](https://bugs.launchpad.net/ubuntu-cdimage/+bug/677260)

> If the EFI bootloader isn't present in the proper location but efi.img is
    available in boot/grub, extract the EFI bootloader and place it in the 

No idea how it is supposed to be created.

---

