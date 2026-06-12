---
title: "uefi boot dl180 gen9 troubles"
date: 2015-09-06
forum: Installation &amp; Upgrades
---

### Post by dimitry2 on 2015-09-06
Hello,
I have a DL180G9, which comes with a B140i which I do not use, but also has a P440ar which I've configured on RAID5.
ubuntu 14.05 installed fine, but on reboot it does not load the correct efi.
It does not make a difference if I switch to legacy BIOS or UEFI.
What does work is if I manually select boot menu and start grubx64.efi file when browsing in the p440 array.
I also ran update-grub bu to no avail...

My system works, but I can't remote reboot it, because I have to manually select the efi file to boot over and over again...
What am I missing?

---

### Post by dimitry2 on 2015-09-06
Found the solution,

one way or another the efi bootlist was corrupted
sudo efibootmgr -c -L "Ubuntu" -l "\EFI\ubuntu\grubx64.efi"

reboot and all fired up correctly

---

