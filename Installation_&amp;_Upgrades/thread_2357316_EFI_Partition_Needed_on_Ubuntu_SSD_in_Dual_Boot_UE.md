---
title: "EFI Partition Needed on Ubuntu SSD in Dual Boot UEFI Installation?"
date: 2017-03-31
forum: Installation &amp; Upgrades
---

### Post by dswaugh on 2017-03-31
I want to do a dual-boot UEFI install using two separate SSDs, with Mac OS on Disk 1 and Ubuntu 16.04 on Disk 2. Simple question: If I use rEFIt and  install GRUB in the EFI partition of Disk 1, do I still need to create a 500MB FAT32 EFI partition at the beginning of the Ubuntu SSD? Guess I'm just wanting to know if each separate SSD in a dual-boot setup still needs to have its own EFI partition if one is loading both OSes from the EFI partition on the first disk. Thanks much.

---

### Post by ubfan1 on 2017-03-31
You wouldn't need an EFI on the second disk, but it might be nice to have if you wanted to move the disk to another system and boot off it.  Far easier to have one and not need it than to try and add it afterwards.  For that matter, some people also add a 1M grub-bios partition just in case a legacy bootloader might be desired at some point in the future.

---

### Post by Dennis N on 2017-03-31
No, they can share the same EFI system partition. Ubuntu installer will only install the OS using an EFI system partition on the first SATA drive (sda), so you will definitely need to have one on there. Installers for other OSes often will allow installation to a different drive. Case in point: I have two drives, and an EFI system partition on each. Manjaro uses the EFI system partition on the second drive (sdb), while Ubuntu must use the first (sda).

---

### Post by oldfred on 2017-04-01
I agree with ubfan1 on having ESP on every drive. 

And I am one to also have bios_grub on every drive, even if just a data drive.
If one of my smaller 32 or 16GB flash drives I may only use 50 or 100MB for ESP as that is more than enough for one UEFI boot, but not much for multiple boot or  for future use or rEFInd or experimenting with other configurations later.

 Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

---

