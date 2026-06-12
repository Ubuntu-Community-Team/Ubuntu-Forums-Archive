---
title: "can't boot after kubuntu 13.10 installation on preinstalled windows8"
date: 2014-04-14
forum: Installation &amp; Upgrades
---

### Post by David_Pichsenmeist on 2014-04-14
i installed kubuntu via livecd on a laptop with preinstalled windows 8. but i'm not able to boot anymore.
when booting i get:


[FONT=courier new]Minimal BASH-like line editing is supported. For the first word, TAB lists possible...
grub> _


[/FONT]i already try to fix it with boot-repair, but error still exists. my boot info from boot-repair is at [http://paste.ubuntu.com/7249967/](http://paste.ubuntu.com/7249967/)
please help!

thanks,
david

---

### Post by oldfred on 2014-04-14
Did you install in UEFI mode or BIOS. Windows would be UEFI if pre-installed and better to have both installs in UEFI boot mode.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Is fast boot off in Windows which is always on hibernation?
Is secure boot off. Should not have to be if you installed Kubuntu in UEFI mode when booted in secure boot mode, but there are some issues of booting Windows from grub with secure boot on. Best to have it off for now.


If you run Boot-Repair.
 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

