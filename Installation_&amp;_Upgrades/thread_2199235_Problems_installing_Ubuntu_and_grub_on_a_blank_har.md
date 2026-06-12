---
title: "Problems installing Ubuntu and grub on a blank hard drive"
date: 2014-01-12
forum: Installation &amp; Upgrades
---

### Post by ninaivk on 2014-01-12
I recently got a laptop with windows 8 installed on it for the purpose of installing Ubuntu or another linux os. I erased the hard drive and tried installing Ubuntu, but the installation ends after it says it cannot install grub. I've looked around forums for solutions to this problem but they are all intended for a dual-boot system.

---

### Post by Bucky Ball on 2014-01-12
Welcome. Even though Win8 is no longer installed, are you still booting the drive in EFI mode? If so, are you attempting to install Ubuntu in Legacy or some other mode apart from EFI?

You have two choices if this is the case: 

Switch off EFI on the disk and install Ubuntu in Legacy mode;
Leave EFI on but make sure you are installing Ubuntu in EFI mode also.

Some BIOS allow for individual devices (like optical drives) to be used in EFI mode.

---

### Post by ninaivk on 2014-01-12
Hi,
I am booting in UEFI and I believe I am installing in that mode as well. Would it be better to use Legacy?

---

### Post by Bucky Ball on 2014-01-12
I don't know about better, but if you are installing Ubuntu in EFI mode, then you need to click 'Something Else' when you get to the partitioning section of the install, partition manually, and create, say, a 300mb FAT32 partition BEFORE /, /home, /swap or any other Ubuntu partitions. Don't call it anything, don't format it. Ubuntu will automagically use that as the EFI partition and install grub to that (I suspect that is the problem).

Issue is EFI doesn't not install to MBR, as such, ALL bootloaders go into the EFI partition. Win8 has one of these by default and the Ubuntu grub then goes automatically into that when installing in EFI mode. As you have wiped the drive, that EFI partition is not there so you need to create it. 

This is an educated guess and worth a try. As for 'is legacy better'? Both have their pros and cons and I can't really answer that. One point is that with legacy you are restricted to any combination of primary and extended partitions but only four on one physical drive. EFI does not have this limitation and allows 128 partitions, primary or extended. 

You'd need to research other pros and cons. ;)

---

