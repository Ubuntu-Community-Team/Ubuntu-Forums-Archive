---
title: "Dual boot with Windows 8: GRUB menu doesn't appear"
date: 2013-08-14
forum: Installation &amp; Upgrades
---

### Post by cathykelly on 2013-08-14
Hi all,

I disabled FastBoot and Secure Boot and installed Ubuntu alongside Windows 8. The computer boots straight into Windows without showing me the GRUB menu. I have to hold shift, restart the computer and select "Use a device" to give me the option to boot into Ubuntu.

I ran Boot Repair, and got a message on launch saying "EFI detected. Please check the options.". When it completed, it gave me this message: "The boot files of [The OS now in use - Ubuntu 12.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. (https://help.ubuntu.com/community/BootPartition)". [http://paste.ubuntu.com/5984616/](http://paste.ubuntu.com/5984616/)

When I restart, it still boots into Windows straight away. Do I need to create a separate boot partition?

Thanks for your help,

Cathy

---

### Post by oldfred on 2013-08-15
I have not seen a UEFI system need the separate /boot partition. That has been an issue with some BIOS and seems to be more often when booting from a external USB drive with BIOS. 

At line 831, Boot-Repair extracts UEFI boot order, but UEFI shows several. I never understood why, but it may be UEFI, UEFI with secure boot,  or BIOS boot order and each can be different? What do you see with different settings for UEFI, UEFI and secure boot, or CSM/BIOS as boot choices? Some UEFI make the settings less obvious as UEFI may mean secure boot and CSM auto boots UEFI if found or then tries to boot CSM/BIOS mode from MBR if no efi partition with boot files.

>  BootOrder: [COLOR=#ff0000]0003[/COLOR],2001
Boot[COLOR=#ff0000]0003[/COLOR]* Windows Boot Manager
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: [COLOR=#ff0000]0000[/COLOR],0003,2001
Boot0003* Windows Boot Manager
Boot[COLOR=#ff0000]0000[/COLOR]* ubuntu



One shows BootOrder with 00003 first which is Windows. The other shows 0000 which is Ubuntu?

---

