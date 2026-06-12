---
title: "Disable/Ignore internal SATA controller for Install"
date: 2017-07-15
forum: Installation &amp; Upgrades
---

### Post by Axxon95 on 2017-07-15
Is there a way to pass an argument to ignore the internal SATA controller?
There isn't any problem with it, I just can't disable it in my UEFI for the install. It's time consuming to remove or disconnect the SSD from my laptop

I'm planning on installing Ubuntu 17.04 x64 on a USB 3 HDD(plenty fast enough, already ran benchmarks on it) and I don't want it to conflict with or see my Windows 10 install. It's only a 240GB SSD so I'm not going to dual-boot.

---

### Post by oldfred on 2017-07-15
I do not disconnect internal drives when installing to external flash drive. It just is a bit easier.

It will create a new folder in your ESP on sda - /EFI/ubuntu and add entries into UEFI.
Folder is not large, and easily deleted, but you must copy that to the ESP on the external drive before deleting. And then copy again into ESP but a new folder /EFI/Boot and rename shimx64.efi to bootx64.efi. UEFI only boots external drives from /EFI/Boot/bootx64.efi which you cannot create during grub install.

Only other choice is not to install grub at all. And then manually install grub to external drive's ESP. And you have to manually create a small configfile grub.cfg to find the full grub.cfg in your install.

You are dual booting if you have two installs, even if on different drives.

You must partition USB drive in advance using gpt partitioning and include an ESP - efi system partition on the USB drive as first partition.

       UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad
And Ubuntu's UEFI grub only installs to the ESP on sda, or not the external drive and not to /EFI/Boot/bootx64.efi. For my PC UEFI full install to a flash drive I manually copied /EFI/ubuntu on sda's ESP to flash drive's ESP. Then copied it again to /EFI/Boot and renamed shimx64.efi to bootx64.efi. I then updated fstab to have correct UUID for ESP on external drive. 

See also link below in my signature.

---

### Post by QIII on 2017-07-15
Hello!

You can tell the installer where to install Ubuntu and GRUB (or not).

But it's my opinion that unplugging your Windows drive, no matter how difficult, is the best way to avoid the significant emotional event of accidentally over-writing your Windows installation.  Do yourself a huge favor and just avoid the risk.  Disconnect the other drive.  Just my opinion.

---

### Post by Axxon95 on 2017-07-15
There isn't anything too important on my SSD, just a couple of large games really.
Because of that I went ahead and tried to install Ubuntu on the USB3 HDD.
I used GNOME Disks to format a 512MB section as EFI System, and used the Ubuntu installer to install GRUB to that(like Q mentioned) and format the rest of the space for / as EXT4 and it installed successfully.
Currently on Ubuntu right now.
Already tested: I can boot Windows and Linux separately just by removing my USB HDD and using my UEFI's EFI Boot manager instead of Windows. 
It didn't touch my Windows Boot Manager at all. Which I'm very much happy with. With this knowledge, in the future on my other UEFI machines I can likely install Ubuntu on other partitions and drives without messing with Windows Boot Manager.

---

