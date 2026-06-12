---
title: "Installing on a Singleboard Computer"
date: 2024-03-24
forum: Installation &amp; Upgrades
---

### Post by z3r01988 on 2024-03-24
Hello,

need some assistens installing Ubuntu Server. 

Stating the USB driver with F7: UEFI: USB-Drive after that im getting: 
error: file '/boot/' not found.
error: can't find command 'grub_platform'.

In GRUB Menu i choose install Ubuntu server, but it stuck on a massage: EFI stub: Loaded initrd from LINUX_EFI_INITRD_MEDIA_GUID device path
I see the USB-Drive blink 3 times and my System frezzes. 

Tried with some Bootparameters: [COLOR=#0D0D0D][FONT=Söhne]acpi=off, [/FONT][/COLOR][COLOR=#0D0D0D][FONT=Söhne]noapic, [/FONT][/COLOR][COLOR=#0D0D0D][FONT=Söhne]nolapic, [/FONT][/COLOR][COLOR=#0D0D0D][FONT=Söhne]pci=nomsi, [/FONT][/COLOR][COLOR=#0D0D0D][FONT=Söhne]i915.modeset=0
[/FONT][/COLOR]but all stuck at the same spot.

How to Debug the installation?

I can install Windows and boot it with no problems at all.

---

### Post by MAFoElffen on 2024-03-24
"Which" singleboard computer, with what architecture?

---

### Post by z3r01988 on 2024-03-24
Can't really tell which CBS it is but its a i5-8365U so x64

---

