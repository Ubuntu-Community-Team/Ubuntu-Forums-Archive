---
title: "Unable to install Bootloader"
date: 2018-01-14
forum: Installation &amp; Upgrades
---

### Post by Mr Puffin on 2018-01-14
Hello everyone this is an interesting issue (not exclusive to Ubuntu as tried various distros but primarily what i'm installing) 

The issue being is every time i try to install systems on my Computers yes plural i'm getting errors installing boot loader i bypassed this slightly by installing the boot loader in vmware to a physical disk  (SD card) then using it on my netbook to boot the failed install
ive tried to wipe entirely on 2 of the 3, ive tried efi and bios boot, and tried 20 different configurations for boot loader install on all pc's with different disc configs

i have tried on multiple computers all same issue
1 My Lenovo Stick 300 
2 My HP Stream 11 netbook
3 My Custom Desktop (Dualboot with Win10.... well trying)

basically i want to know what is happening why is the only computer i have that installs reliably my MacBook Pro?.....

---

### Post by oldfred on 2018-01-15
If only installing in VM, I will move to that sub-forum. 
Do not know VM type installs.

Are you installing in UEFI or BIOS boot mode?
Are you using gpt partitioning which requires the ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot.
If MBR partitioning, you probably would not be getting any error, but that would be BIOS boot only.

If UEFI more info in link below in my signature.

---

