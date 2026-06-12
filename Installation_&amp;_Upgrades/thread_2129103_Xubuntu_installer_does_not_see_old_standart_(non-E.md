---
title: "Xubuntu installer does not see old standart (non-EFI/GPT) partitions on a hard disk"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by Zetruger on 2013-03-25
I'm trying to install Xubuntu 12.04 LTS on a new notebook *HP ENVY m6*[COLOR=#171717][FONT=arial]-1262er ([/FONT][/COLOR]*D2G42EA*[COLOR=#171717][FONT=arial]) from a bootable cd.
And the installer does not see old standart ([/FONT][/COLOR][COLOR=#171717][FONT=arial]non-EFI/GPT[/FONT][/COLOR][COLOR=#171717][FONT=arial]) partitions on the hard disk.
[/FONT][/COLOR][COLOR=#171717][FONT=arial]
In the BIOS Boot options the legacy boot mode is enabled.
But the BIOS uses [/FONT][/COLOR][COLOR=#171717][FONT=arial]the legacy boot mode only after [/FONT][/COLOR][COLOR=#171717][FONT=arial]EFI.

I think there is no problem with old bootable CDs.[/FONT][/COLOR]

---

### Post by Bashing-om on 2013-03-25
Zetruger; Hi ! Welcome to the forum .

How bout this thought. The "older" disk partitioning schemes only permitted a max of 4 primary partitions per hard disk. Are you attempting to dual boot with windows, such that presently windows is using all 4 of the partitions ?
To see: 
Fire up ubuntu in "try ubuntu" mode: Launcher ->dash -> search term "GParted" -> icon to launch ubuntu's partition editor;
If you need help interpreting the display, post the screen shot, and standby for additional terminal commands.[INDENT=4]
just try'n to help

[/INDENT]

---

### Post by darkod on 2013-03-25
If you don't want to use uefi, i suggest you disable it if possible. That way you are sure you won't boot the ubuntu cd in uefi mode.

Otherwise, use your machine one time boot menu (F12 or which ever key you need) and select to boot from the legacy cd-rom, not the uefi cd-rom (there will be two versions on uefi capable boards).

That will make sure ubuntu is installed in legacy mode because it installs in which ever mode you boot the cd.

As for the disk partition table, you can use msdos or gpt as you wish. Ubuntu can work with both in legacy boot, unlike windows. If you don't need any data from the disk I would boot the ubuntu cd in live mode first and write a new msdos or gpt table on the disk. This will make it sure it's done properly because if you used only windows tools on this disk they can mess up switching from gpt to msdos table, they don't delete the backup gpt table.

On gpt disks you will need a small 1MiB partition with no filesystem (RAW) and with the bios_grub flag set because grub2 will need it for part of its code. A gpt MBR is smaller than msdos so it doesn't fit there.

---

