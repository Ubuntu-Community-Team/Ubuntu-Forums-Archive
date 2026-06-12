---
title: "Needs assistance on installing Ubuntu on a GPT Hard Drive"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by cyclonous_gt on 2011-10-04
Guys,
    I would like to install Ubuntu on a single 2TB Harddrive with below partitioning. However, when I have finished installing my Ubuntu on a UEFI enabled pc, a ¨No Bootable device¨ error is displaying during its POST.  I have gone through the web searching for a detailed procedure on installing Ubuntu on a GPT drive and UEFI enabled BIOS but to no avail I have failed in my effort to acquire my goal.  What I have done so far that is closed to my goal is I have boot on Supergrub2 (burn the iso available on the net on a cd and used a usb cdrom and enabled first boot to the usb device) and from there I could boot my Ubuntu installed on the GPT Drive.

Partition 1 (EXT4, 70GB - activated as root /)
Partition 2 (2GB Swap Area)
Partition 3 (1.9TB EXT4 - to serve as my file/backup depot)

I´am new to GPT and UEFI and have no experience yet on this file system and boot loader. I would greatly appreciate any help and assistance on our experts here in the forum.

Thanks in advance and God Bless...:p

---

### Post by oldfred on 2011-10-05
I boot gpt but with the old style BIOS not UEFI. But with BIOS you have to have a bios_grub partition and with UEFI you have to have an efi partition. You do not mention either.

How boot a (U)EFI system natively (without BIOS CSM) using GRUB 2
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

EFI boot loader information - srs5694 & skodabenz
[http://ubuntuforums.org/showthread.php?t=1849160](http://ubuntuforums.org/showthread.php?t=1849160)
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")

---

