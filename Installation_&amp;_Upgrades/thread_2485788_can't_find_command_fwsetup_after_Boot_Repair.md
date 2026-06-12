---
title: "can't find command fwsetup after Boot Repair"
date: 2023-04-09
forum: Installation &amp; Upgrades
---

### Post by aambrose on 2023-04-09
[http://paste.ubuntu.com/p/vq9JSZyF7n/](http://paste.ubuntu.com/p/vq9JSZyF7n/)

Been trying to solve cascading set of issues:

* Initially, trying to fix the following grub issue on booting linux after an upgrade: Attempt to read or write outside of disk 'hd1' 
* Alas, before using Boot Repair, followed some unfortunate advice which made me lose my windows dual-boot option in the grub menu
* Ran Boot Repair, went through all the steps on [https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk](https://help.ubuntu.com/community/InstallingUbuntuOnBigDisk)
  - none of the steps worked:  only linux found, and attempting to boot linux got same error as above
  - finally ending up on step 3:  creating a new 1GB boot partition
  - now getting new error; only UEFI Firmware Settings shown, and "Can't find command fwsetup" is now what I'm getting

* Checked BIOS settings to make sure UEFI settings were enabled.

---

### Post by TheFu on 2023-04-09
**fwsetup** isn't a normal Ubuntu command. Perhaps you are confusing it with some other command?

Nothing special is required to install Ubuntu on huge disks and hasn't been for about 15 yrs.

---

### Post by oldfred on 2023-04-09
You have mixed UEFI boot and BIOS boot which usually leads to issues.
I think fwupd is only for UEFI systems.

You show UEFI boot entries in UEFI boot menu, but ESP - efi system partition it wants to boot from sdb1.
But sdb1 is flagged as bios_grub for BIOS boot which normally should be only 1MB and unformatted, but is 36,864 sectors.

Your Windows in sda looks like a BIOS/MBR install.
Windows only installs & boots in BIOS mode from MBR partitioned drives.
Windows only installs & boots in UEFI mode from gpt partitioned drives. 
Microsoft has required vendors to install in UEFI/gpt mode since 2012, so did you manually overwrite Windows with a BIOS install?

You may be able to convert sdb1 back to FAT32 with esp,boot flags & reinstall grub with Boot-Repair or chroot. But that will not boot Windows in BIOS mode as once you start booting you cannot change boot mode.

---

### Post by aambrose on 2023-04-09
[solved]

Decided to push the big red button and re-installed linux from scratch.  That fixed it!  :)

---

### Post by aambrose on 2023-04-09
Oh hey; this is very helpful, thanks!  

So, just so I'm clear:  I'm not _required_ to boot Windows in BIOS mode, correct?   It's just a nice-to-have, perhaps if I want quick boot or something like that?   If so, I don't care about that; I just want a dual boot that's functional.

Oh, and yes, I'm totally aware that my disk arrangement is a mess, and probably needs some re-jiggering.  :)

---

### Post by yancek on 2023-04-10
Booting windows in Legacy/CSM mode with the boot code in the MBR requires an msdos partition table not gpt.  With a gpt partition table, windows must be installed in UEFI mode to boot.  If you want to boot windows from Grub, the Linux install must be in the same mode as windwos, Legacy or UEFI for both, as pointed out above.  If you have windows on one drive and Linux on another you can select the drive in the BIOS firmware.  The two windows drives (sda and sdc) are both dos while the Linux is GPT

---

