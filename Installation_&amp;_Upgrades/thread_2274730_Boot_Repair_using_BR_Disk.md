---
title: "Boot Repair using BR Disk"
date: 2015-04-21
forum: Installation &amp; Upgrades
---

### Post by Muhammad_Ahmad_Mujtaba on 2015-04-21
[FONT=tahoma]Hi,
[URL="http://paste.ubuntu.com/10864386/"]http://paste.ubuntu.com/10864386/

[/URL]Above is output of running Boot repair disk using default

and

Below is advanced:
Things done:
OS Default: Windows 8.1
Update GRUB2 to latest version ticked.
Timeout = 20sec.

[http://paste.ubuntu.com/10864369/](http://paste.ubuntu.com/10864369/)
[/FONT]

---

### Post by oldfred on 2015-04-21
It looks like you have several Linux installs and a Windows partition.
But drive is now gpt partitioned with grub in the gpt protective MBR and a bios_grub partition for BIOS boot.
But on gpt partitioned drives Windows only boots in UEFI mode.
Ubuntu can boot in either UEFI or BIOS depending on how you install and if gpt has an efi partition for UEFI boot or a bios_grub partition for BIOS boot.
Similar with Windows you must have an efi partition and boot its installer in UEFI mode to install in UEFI mode.
UEFI suggests that efi partition be first or at least near beginning of the drive. Was sda3 an efi partition before, it does not now have boot flag that would make it an efi partition.

What is your issue?

---

### Post by Muhammad_Ahmad_Mujtaba on 2015-04-22
Hi thanks for answering, I have machine of 2010 which has BIOS not UEFI.
My problem is that ON GPT PT, I want to tri-boot Linux Mint and Ubuntu 15.04 (in place of Elementary OS) with Windows 8.1
but does not matter which method I apply nothing happens.

I tried to prepare Windows bootable pen-drive and ran

bootrec.exe /rebuildbcd
bootrec.exe /fixMbr
bootrec.exe /fixboot

which said boot has been recovered but on re-running boot repair nothing happened at all.
furthermore, I installed ubuntu in place of elementary OS which has read Linux Mint but not windows.

What else I should do?

---

### Post by oldfred on 2015-04-22
You cannot use gpt partitioning with Windows in BIOS boot mode.
Only Linux systems boot from gpt drives with either UEFI or BIOS.

Most install Windows to a MBR(msdos) drive and have Ubuntu on gpt partitioned drives.
If you only have one drive you must repartition entirely to MBR. Back everything up and reinstall.

You may be able to convert, but I never have done it.
       Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. Besure to have good backups - srs5694
[http://ubuntuforums.org/showthread.php?t=1718966](http://ubuntuforums.org/showthread.php?t=1718966)
Use parted or gparted to remove gpt if no data to save:
[http://ubuntuforums.org/showthread.php?t=1719851&page=2](http://ubuntuforums.org/showthread.php?t=1719851&page=2) post #20
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)

---

