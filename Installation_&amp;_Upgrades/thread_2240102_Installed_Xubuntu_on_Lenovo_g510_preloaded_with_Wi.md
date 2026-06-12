---
title: "Installed Xubuntu on Lenovo g510 preloaded with Win 8..."
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by Flyersrock87 on 2014-08-17
... and Win 8 no longer boots.  The error I'm getting when I attempt to boot to Windows is "0xc000000e."

I tried running the boot-repair utility (and followed with "sudo update-grub"), to no avail.

Here is the output of my boot-repair:  [http://paste.ubuntu.com/8076079/](http://paste.ubuntu.com/8076079/)

Any advice?  Any other information you might need?

---

### Post by oldfred on 2014-08-17
First undo the 'buggy' UEFI fix from Boot-Repair.

       Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)

To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

It looks like you originally installed Ubuntu in BIOS boot mode. But with Windows in UEFI boot mode you really need Ubuntu in UEFI mode. And it looks like Boot-Repair converted you to UEFI boot mode. Just be sure to always be in UEFI boot mode. Usually  better to have secure boot off for now.

You should have in UEFI menu or one time boot key both Ubuntu & Windows as boot options in UEFI mode.

It also looks like you booted Boot-Repair in Legacy/BIOS/CSM mode. You need to boot in UEFI mode.

---

