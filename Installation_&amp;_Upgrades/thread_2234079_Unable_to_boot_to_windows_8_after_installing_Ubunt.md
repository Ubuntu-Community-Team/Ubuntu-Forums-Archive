---
title: "Unable to boot to windows 8 after installing Ubuntu 14"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by arunkam on 2014-07-12
Hi

I installed ubuntu recently and ever since then I have been unable to access windows.I followed various discussions online and tried using boot-repair.It still didnt fix my problem.

here is the boot-repair info : [http://paste.ubuntu.com/7147869/](http://paste.ubuntu.com/7147869/)

Please help.

Thanks in advance.

---

### Post by oldfred on 2014-07-12
What model computer.

It looks like you left Windows in hibernated state. You must turn off the fast boot if dual booting.
       [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

You have run Boot-Repair's buggy UEFI fix. That renames the Windows efi boot file to directly boot grub when UEFI has been modified by vendor to only boot Windows. There are several other work arounds that may be better.

To be able to boot Windows from UEFI menu so you can turn off fast boot, you need to undo the rename. If you can directly boot the ubuntu entry in UEFI menu then you do not need any work around/fixes.

      
 Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

