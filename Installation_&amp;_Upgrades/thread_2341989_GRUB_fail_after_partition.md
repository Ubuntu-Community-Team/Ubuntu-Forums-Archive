---
title: "GRUB fail after partition"
date: 2016-11-02
forum: Installation &amp; Upgrades
---

### Post by ss4gohan22 on 2016-11-02
Can anyone help me with this? My main problem is that my computer cannot  find my ubuntu OS(15.xx). I modified my partitions from the windows 10  side of my computer using partition magic as I was trying to increase  the size of my linux partition. Now I can't get in as it says GRUB  failed. I tried to use the boot repair while running from a live ubuntu  usb (16.04) but it says by bios is in legacy and I should change it to  EFI. I changed it to UEFI (originally a windows 8 PC) and it says the  same thing and I don't believe I have EFI in my bios. I know ubuntu is  in sda10 and that my windows is sda5. When I do advanced options, it  looks like it will fix my problem but I would ask first before I  continue.

Here is the link to the report from boot-repair: [http://paste2.org/47kJOEZE](http://paste2.org/47kJOEZE)

---

### Post by oldfred on 2016-11-02
Always use Windows tools for Windows.
And always use Linux tools for Linux.

You show grub installed to MBR for BIOS boot, but without bios_grub partition with gpt partitioning it will not install correctly for BIOS boot.
But since Windows is UEFI you really want UEFI boot.
Be sure to boot install media (live installer) in UEFI mode. Report says you booted in BIOS/CSM/Legacy mode.
Then run Boot-Repairs' advanced mode to totally uninstall grub-pc(BIOS) and install (grub-efi-amd64(UEFI).

UEFI should show two boot option for Ubuntu's live installer. One is UEFI:flashdrive and other is flashdrive or just plain old (BIOS). Flash drive may be name or label of flash drive you have installed Ubuntu live installer into.

---

