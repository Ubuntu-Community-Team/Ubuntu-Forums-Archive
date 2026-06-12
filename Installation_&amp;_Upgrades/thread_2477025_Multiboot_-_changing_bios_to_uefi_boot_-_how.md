---
title: "Multiboot - changing bios to uefi boot - how"
date: 2022-07-12
forum: Installation &amp; Upgrades
---

### Post by hornetster on 2022-07-12
Have a multiboot system - Tumbleweed - Ubuntu 22.04 - Win10.
Have converted from MBR/BIOS boot to GPT/UEFI, and all working fine in Tumbleweed (my main OS).
How do I update my Ubuntu 22.04 install to successfully boot via UEFI?
Believe I probably need a /boot/efi directory and some software installed? (Prob should have checked before I went ahead.)
Once I have Ubuntu working, will have to reinstall Win as well, I'm assuming, then rescuscitate grub again...
Thanks.

---

### Post by oldfred on 2022-07-13
If one drive all systems share the same ESP - efi system partition which is FAT32 with boot,esp flags in gparted.
What is tumbleweed based on? Is it booting in UEFI or BIOS mode on gpt partitioned drive?

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Windows only boots in UEFI mode from gpt partitioned drives & only boots in BIOS mode from MBR(msdos) partitioned drives.
Drive conversion from MBR to gpt, normally totally erases entire drive. Be sure to have good backups.

---

### Post by hornetster on 2022-07-13
> **oldfred said:**
> If one drive all systems share the same ESP - efi system partition which is FAT32 with boot,esp flags in gparted.
What is tumbleweed based on? Is it booting in UEFI or BIOS mode on gpt partitioned drive?

Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)   &           
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Windows only boots in UEFI mode from gpt partitioned drives & only boots in BIOS mode from MBR(msdos) partitioned drives.
Drive conversion from MBR to gpt, normally totally erases entire drive. Be sure to have good backups.

Thanks for the response.
Have basically got it all up and running, now.

Tumbleweed was working OK, and used diskpart, and bcdboot to manually add the required stuff for Windows. Unfortunately that then overwrote Tumbleweed (expected...), so used the Tumbleweed install disk to boot Tumbleweed (what a great thing, is the tumbleweed ISO!!), and rewrote the tumbleweed grub.
Then used the Boot Repair ISO to add Ubuntu.

All now working, and just fine tuning...
Thanks.

---

