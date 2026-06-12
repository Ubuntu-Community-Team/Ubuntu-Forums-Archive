---
title: "&quot;All boot options were...&quot; error after trying to create a dual-boot - Boot-repair log"
date: 2022-02-23
forum: Installation &amp; Upgrades
---

### Post by rpieslak on 2022-02-23
Greetings

After trying to install a Dual-Boot I got the booting error "All boot options were tried"

I created an iso with boot-repair and generated a log which is here: [https://pastebin.ubuntu.com/p/XCrXGCnBpf/](https://pastebin.ubuntu.com/p/XCrXGCnBpf/)

I appreciate any help on this matter. 

Thank you.

---

### Post by tea for one on 2022-02-24
[COLOR="#0000FF"]Line 115[/COLOR] - 1 OS detected
[COLOR="#0000FF"]Line 117[/COLOR] - OS#1:   Windows 10 or 11 on sda3 

[COLOR="#0000FF"]Line 123[/COLOR] - The only mention of Ubuntu is here (live session)

[COLOR="#0000FF"]Lines 130 - 136[/COLOR] - No sign of Ubuntu EFI files in ESP

The following line is unexpected in an attempt to dual boot Windows and Ubuntu?
[COLOR="#0000FF"]Line 266[/COLOR] - sda10 fedora_localhost-live 

Nevertheless, as only Windows has been detected and based on the comment [highlight]All boot options were tried[/highlight]:-

Back up your data using an Ubuntu live session.
Prepare a Windows repair disk
Repair or re-install Windows
Double check that Windows is functioning OK.

When you are happy that Windows is in order, boot into an Ubuntu live session and run from a terminal:-
```
sudo parted -l
```

Post the output in code tags in this thread so that other forum members can help with installing Ubuntu.
The partition layout from your pastebin report seems excessively complicated for a Windows/Ubuntu dual boot.

---

### Post by oldfred on 2022-02-25
You have UEFI system.
Do not mix UEFI mode installs with BIOS/legacy/CSM mode.

You have UEFI boot entries for Windows & Debian. But Debian UEFI grub entry goes to partition that does not exist, so will never work.
If you cannot boot Windows from UEFI boot menu, you need your Windows repair flash drive. Boot-Repair is for reinstalling grub for Linux systems. And must be booted in UEFI mode for your system.

You have grub installed to protective MBR and a bios_grub partition for BIOS boot.

Always boot live installer or Windows repair flash drives in UEFI boot mode.

---

