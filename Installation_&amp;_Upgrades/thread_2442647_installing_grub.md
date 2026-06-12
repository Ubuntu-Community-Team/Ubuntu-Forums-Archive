---
title: "installing grub"
date: 2020-05-06
forum: Installation &amp; Upgrades
---

### Post by forggameplaying on 2020-05-06
I want to install ubuntu 20.04OS on external SSD drive. I managed to create dvd bootable media on my own and installed ubuntu 20.04 desktop iso version on it. However there's a little problem accosiated with installing grub bootloader. It does not installing. I tried to set sdb,sdb1, sdb2, and every other possible partition as partition to install bootloader, but it does not install how to deal about it? 
I want to you to make clear how to do it manually. Should I install bootloader on partition mounted on /boot or something else?! and what filesystem it should be?

---

### Post by yancek on 2020-05-06
If you are installing Ubuntu on an external drive does that mean you have some other OS installed on an internal drive?  If so, what is it?  Also, is the OS on the internal drive an EFI install or a Legacy install?

---

### Post by oldfred on 2020-05-06
Post this, in addition to whether UEFI or BIOS install;
sudo parted -l

---

### Post by forggameplaying on 2020-05-07
well, It is windows 10(UEFI) installed on my laptop and I want to use MBR BIOS grub install on my external drive. But does it make sense?

---

### Post by CelticWarrior on 2020-05-07
No, mixing modes doesn't make sense.

You can install Ubuntu in the external drive and use the internal drive ESP (EFI System Partition) for the bootloader (Grub). It will work in that same computer though. If you want portability and the ability to also boot in older BIOS computers the process is a lot more complicated but doable.

---

### Post by oldfred on 2020-05-07
You can, but only because they are separate drives.

I would at minimum suggest you use gpt partitioning, and include both an ESP for UEFI boot and a bios_grub for BIOS boot.
Then you can convert install from BIOS to UEFI or UEFI to BIOS, just by reinstalling the correct version of grub.
There is grub-pc for BIOS boot and grub-efi-amd64 for 64 bit PC boot in UEFI mode.

Depending on size of external drive 100 to 500MB for ESP, 1 or 2MB for bios_grub and if not large just one ext4 partition for / (root). If larger drive then 25 to 30GB for / and rest for /home and/or data partition(s). 

I started converting drives to gpt back in 2010. I still had XP which required MBR, but then reformatted another drive to gpt and installed Ubuntu in BIOS boot mode. Then when Windows required UEFI systems in 2012, I started adding both the ESP & bios_grub to all drives assuming later I would have UEFI and want gpt to boot in UEFI mode. It was 2014 before I has an UEFI system, but almost all drives by then were gpt.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

