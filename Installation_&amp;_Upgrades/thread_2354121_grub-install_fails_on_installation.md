---
title: "grub-install fails on installation"
date: 2017-02-28
forum: Installation &amp; Upgrades
---

### Post by idquod on 2017-02-28
I'm trying to install ubuntu to replace another linux distro on a dual boot with windows 10. I set up the other linux distro (Arch linux) long ago and I don't really remember exactly how I configured it but I think an iteration of GRUB is already first in the boot chain and it gives both the Windows Boot Manager and (formerly) Arch linux as options to boot into. I've tried several times to install ubuntu using a liveUSB but each time it fails with the following error:

```
Feb 28 12:31:03 ubuntu grub-installer: grub-install: error: cannot open `/boot/efi/EFI/ubuntu/shimx64.efi': No such file or directory.
Feb 28 12:31:03 ubuntu grub-installer: error: Running 'grub-install  --force "/dev/sda"' failed.
```

which seems related to this previous error message:
```
Feb 28 12:30:23 ubuntu ubiquity: mkdir: cannot create directory ‘/boot/efi/EFI/ubuntu’
Feb 28 12:30:23 ubuntu ubiquity: : Read-only file system
Feb 28 12:30:23 ubuntu ubiquity: Installing fwupx64.efi to EFI system partition.
Feb 28 12:30:23 ubuntu ubiquity: cp: cannot create regular file '/boot/efi/EFI/ubuntu/fwupx64.efi'
Feb 28 12:30:23 ubuntu ubiquity: : No such file or directory
```

The installer is set to install the boot manager at /dev/sda wherein fall all my partitions /dev/sda1, /dev/sda2... I've also tried creating a separate partition from which to boot from and received the same message.

Any help would be appreciated !

---

### Post by yancek on 2017-02-28
Do you have windows 10 and Arch installed using UEFI or the older MBR?  If you boot Ubuntu from the usb, you can open a terminal to run:  sudo gparted which will open the partition manager to show the various partitions.  If you are using UEFI, one of the partitions should show as 'EFI'.  If the current systems installed are 'not' EFI, you will have serious problems booting if you install Ubuntu UEFI.  The link below gives a lot of useful information on dual-booting using UEFI/Ubuntu.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by idquod on 2017-02-28
Arch and Windows are installed using UEFI, the EFI partition is at /dev/sda1.

I tried boot-repair as well and got the following error:

```
Reinstall the grub-efi-amd64-signed of sda7
Installing for x86_64-efi platform.
grub-install: error: cannot open `/boot/efi/EFI/ubuntu/shimx64.efi': No such file or directory.
grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot : exit code of grub-install :1
Error: no grub*.efi generated. Please report this message to boot.repair@gmail.com
```

Here's a pastebin of boot-repair's output if that would help:
[http://pastebin.com/2XGmja0A](http://pastebin.com/2XGmja0A)

---

### Post by oldfred on 2017-02-28
Boot-Repair has changed your fstab, for efi partition to defaults. 
On reboot, it now should be read/write. It was set to 0077 and read only.
> UUID=FE34-3E99  /boot/efi   vfat    defaults    0   1

Try using Boot-Repair again after reboot.

I found just remounting after changing from 0077 to defaults does not work, you have to reboot.

If still an issue you may need to run fsck. Change example with sdb1 to your ESP/efi/FAT32 partition.
       sudo fsck.vfat -t -a /dev/sdb1

---

### Post by idquod on 2017-02-28
I tried rebooting after running boot-repair and running it again, but it failed with the same error.

> **oldfred said:**
> If still an issue you may need to run fsck. Change example with sdb1 to your ESP/efi/FAT32 partition.
       sudo fsck.vfat -t -a /dev/sdb1

fsck appears to fail giving me the error? :

```
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
...
Not automatically fixing this.
```

---

### Post by oldfred on 2017-02-28
Not seen that error/warning.
Not sure if issue or not.

See if chkdsk from Windows give different results.
Windows does not show ESP by default, you have to mount it first.

---

