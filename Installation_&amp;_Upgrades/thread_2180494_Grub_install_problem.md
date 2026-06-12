---
title: "Grub install problem"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by m8m6 on 2013-10-13
Hello everyone,

I've installed Ubuntu 13.04 on a Lenovo Ideapad S300.
At the boot up, Win8 recovery thingy is automatically fired up, with no option to boot into Ubuntu.
Plugged in the liveUSB and performed the boot-repair installation procedure from terminal, but it gives me the following error:
[I]
EFI detected. Please use Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")) which contains an EFI-compatible version of this software.[/I]

On the other hand, the report option works, and here's the output:
[http://paste.ubuntu.com/6228291/](http://paste.ubuntu.com/6228291/)

From the look of it, it's seems I'm missing the grub, though in /dev/sda8 (ubuntu partition) it says it's installed.

I've checked already the forums, but to no avail.
Thanks in advanced for any input.

m.

---

### Post by grahammechanical on 2013-10-13
Have you followed the advice to use a 64 bit Boot-Repair disk? The Boot-Repair software that you have cannot repair what its wrong because it does not contain EFI-compatible Boot-Repair software.

Notice this advice.

> [COLOR=#666666]===================[/COLOR] Repair blockers
EFI detected. Please use Boot-Repair-Disk-64bit [COLOR=#666666]([/COLOR]www.sourceforge.net/p/boot-repair-cd[COLOR=#666666])[/COLOR] which contains an EFI-compatible version of this software.
[COLOR=#666666]===================[/COLOR] Advice displayed in [COLOR=#AA22FF]**case **[/COLOR]of recommended repair
The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
Do you want to [COLOR=#AA22FF]**continue**[/COLOR]?
[COLOR=#666666]===================[/COLOR] Final advice in [COLOR=#AA22FF]**case **[/COLOR]of recommended repair
Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sda2/efi/.../grub*.efi file!

[COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair
This setting would purge [COLOR=#666666]([/COLOR]in order to fix packages unsign-grub[COLOR=#666666])[/COLOR] and reinstall the grub-efi of sda8, using the following options: sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    backup-and-rename-efi-files

Regards.

---

### Post by oldfred on 2013-10-13
Welcome to the forums.

It seems you have installed grub2's boot loader to the PBR of sda8. You need grub installed to the efi partition when installed with UEFI. As grahammechanical has suggested you need to boot Boot-Repair in UEFI mode.

How you boot installer and Boot-Repair is how they install or repair. You must have booted installer in BIOS/CSM/Legacy mode not UEFI mode.

Boot-Repair converts a BIOS install to UEFI by uninstalling grub-pc and installing grub-efi.

---

