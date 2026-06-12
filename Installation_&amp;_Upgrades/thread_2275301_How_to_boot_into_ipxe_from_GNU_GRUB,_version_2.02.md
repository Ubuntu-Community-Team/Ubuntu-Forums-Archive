---
title: "How to boot into ipxe from GNU GRUB, version 2.02?"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by Mr_Installer on 2015-04-25
Hello everyone!

I am trying to boot into ipxe network boot firmare (ipxe.efi) from GRUB2 bootloader. Does grub2 has the ability to load arbitrary UEFI executables? If yes, then what commands should I use to boot my ipxe.efi image. Any help would be appreciated. Thanks in advance! ;)

---

### Post by oldfred on 2015-04-25
You posted in the tutorial sub-forum where instructions only are posted. 
Moved to Installation.

Grub does have one default entry to get into UEFI. Not sure about any others.

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###


I thought UEFI could directly boot network device? Never tried it.

 Boot0007* UEFI:Network Device	BIOS(83,0,00)

---

### Post by Mr_Installer on 2015-04-25
> **oldfred said:**
> You posted in the tutorial sub-forum where instructions only are posted. 
Moved to Installation.

Grub does have one default entry to get into UEFI. Not sure about any others.

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###


I thought UEFI could directly boot network device? Never tried it.

 Boot0007* UEFI:Network Device    BIOS(83,0,00)

First of all, thanks for moving my topic into right direction))

**I am trying to make a following setup:**

_*Start up a PC in UEFI mode only, using HDD/USB drive -> grubx64.efi (extracted from most recent ubuntu Desktop x64 LTS live cd) -> GRUB 2 -> menuentry 'start iPXE' {??? ipxe.efi} -> ...*_

Just looked through all available commands in GRUB (2.02) and didn't find, mentioned 'fwsetup'.

I know that it is possible to boot ipxe from the network directly (e.g. TFTP server), but it doesn't really suit my needs. Any other ideas?

Below, I attached a screenshot of what I tried so far to make it work (Booted into Virtualbox Guest machine using flash drive ), but with no luck.

[ATTACH=CONFIG]261540[/ATTACH]

---

### Post by oldfred on 2015-04-25
If copying grub into an efi partition you need all of it. I did that with a grub only UEFI boot flash drive. But it expects to find all the folders & files as it is full grub.

The instructions on creating grub have many options which I have not tried. And some of those limit the number or need for the .mod files.
see
man grub-install
or
info grub-install

---

