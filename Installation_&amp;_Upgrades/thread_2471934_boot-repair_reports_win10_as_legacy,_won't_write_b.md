---
title: "boot-repair reports win10 as legacy, won't write boot loader"
date: 2022-02-13
forum: Installation &amp; Upgrades
---

### Post by trocanyon on 2022-02-13
I have a dual boot uefi system managed by grub to  boot windows10 and ubuntu.  I decided to upgrade ubuntu but the install failed.  The next time I rebooted ubuntu booted to an (emergency) command mode.  

Examination of the journal (jounalctl -xb) indicated there were a stale UUIDs for the ubuntu and partitions in /etc/fstab so I updated the ubuntu UUID. swap was getting loaded automatically so I removed the swap entry from fstab.  ubuntu still would not boot, it looked like the EFI partion UUID was also stale.

My fix was to update the disc label (of the FAT32 partition) to the stale UUID.  I used a command (maybe mlabel) that did change the label (UUID) but it apparently also corrupted the MBR, so now I cannot boot anything.  

Before I attempted boot-repair I booted ubuntu from CD and ran gparted.  It complained that sda1 was corrupted.  Don't know if it was the right thing to do at this point but I reformatted it thinking I could write a new mbr/bootloader on it.

At one point I was using grub from unbuntu, but a windows upgrade overwrote grub with its own boot loader.  The only way I could recover the linux boot was to install windows grub2.  The short of it is that the windows system has the active grub2 on it, and ubuntu system has a stale grub installation on it.  Should I be trying boot-repair on windows?

I've been trying to use boot-repair (linux) to put grub back, but it is convinced the windows10 system is legacy and suggests that I change the BIOS to non-efi boot mode.  I tried this but then boot-repair failed because it could not delete grub...because grub needs EFI to install.  I don't know which partition to set to the /efi (sda1 or sda3)?  

I changed the BIOS back to efi boot mode and pastebin'd the boot-information log to [https://paste.ubuntu.com/p/sD4VWqzjtW/](https://paste.ubuntu.com/p/sD4VWqzjtW/).

As far as I can tell both systems are generally intact, and I'd love to keep it that way.

---

### Post by oldfred on 2022-02-13
It is saying Windows legacy as it cannot see any Windows UEFI boot entries.
But drive is gpt partitioned and Windows only boots in UEFI boot mode from gpt partitioned drives.

If system was UEFI, then you must  have erased ESP - efi system partition which has Windows boot files and somehow erased UEFI boot entries for Windows & Ubuntu.

You have both an ESP for UEFI boot with no folders for boot files. And it is FAT16 where normally FAT32.
Folders in normal dual boot include /EFI/ubuntu & /EFI/Microsoft.

And you have a bios_grub partition for BIOS boot of Ubuntu on gpt partitioned drive, but it is FAT32 as if it was the original ESP?
A bios_grub partition is unformated and only 1 or 2MB.

I would first try changing sda1 back to an ESP and remove esp flags from sda3. You only can have one ESP per device/drive.
Then report may show UEFI boot files in sda1?

The BIOS boot loader of Windows in gpt's protective MBR, will not ever work with UEFI and gpt. But will never be used, if you to not attempt to boot in BIOS/CSM/Legacy boot mode, so best not to try to delete or change it. The command to erase it, is more dangerous for new users than just leaving it.

After changing esp flags, boot live installer in UEFI mode & rerun Boot-Repair's report. Post that new link.

If Windows was BIOS it had to have MBR partitioning.

---

