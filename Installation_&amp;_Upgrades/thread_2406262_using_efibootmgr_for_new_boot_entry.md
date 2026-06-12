---
title: "using efibootmgr for new boot entry"
date: 2018-11-18
forum: Installation &amp; Upgrades
---

### Post by ranchu-panchu on 2018-11-18
[COLOR=#24292E][FONT=-apple-system]Hello,[/FONT][/COLOR]
[COLOR=#24292E][FONT=-apple-system]I am trying to add boot entry for MBR table (shadow) in SSD.
Using bcfg it is possible to browse to device fs0:\EFI\boot\bootx64.efi (pressing tab will show all the device in current directory).
But we don't have bcfg in our BIOS.
I've tried to add the following:[/FONT][/COLOR]

[LIST=1]
[*]efibootmgr -c -d /dev/sda -p 0 -L "mypba" -l "\EFI\boot\bootx64.efi"
and also the following
[*]efibootmgr -c -d /dev/sda -p 1 -L "mypba" -l "\EFI\boot\bootx64.efi"
But in both cases the UIEFI boot fails to start.
[/LIST]
[COLOR=#24292E][FONT=-apple-system]I guess I might need to add it using --device but I don't know which device match the MBR shadow.
Is it possible to find the device using efibootmgr as it done with bcfg (pressing fs0:\ and TABs)?
The issue/problem is also described here:
[/FONT][/COLOR]
[COLOR=#24292E][FONT=-apple-system]Thank you for any idea,
Ran[/FONT][/COLOR]

---

### Post by oldfred on 2018-11-18
What is a shadow MBR?  Is that your p0 or MBR? The gpt protective MBR?
Normally UEFI used gpt.

UEFI has both BIOS & UEFI boot, but they are not compatible.
Once you start booting in one mode, you cannot switch.

UEFI may need UEFI turned off & BIOS/CSM/Legacy turned on.
But most newer UEFI will see the MBR and automatically have an entry for that. As long as UEFI Secure boot is off.

Attached is an example of two boot entries for one hard drive. One clearly UEFI and then other is the BIOS boot using MBR.

---

