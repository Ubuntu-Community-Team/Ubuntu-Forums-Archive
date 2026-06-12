---
title: "Stuck on Grub CLI even after using Boot Repair Disk"
date: 2024-09-06
forum: Installation &amp; Upgrades
---

### Post by carlossuated on 2024-09-06
I tried to remove my Linux partition from windows since I had dual boot and wanted more space.
I removed the partition and extended the windows volume but forgot to uninstall grub.
Whenever I start my pc I am directed to the Grub CLI and can’t do anything to exit it, I already tried many solutions with no result, also used boot repair disk which gave me this report: [https://pastebin.ubuntu.com/p/4ntHsg89Hk/](https://pastebin.ubuntu.com/p/4ntHsg89Hk/)

Thank you in advance

---

### Post by oldfred on 2024-09-06
Since HP, you have to go into HP's settings & change UEFI boot order. 
HP - <kbd>escape</kbd>  + <kbd>F9</kbd> for UEFI boot menu, <kbd>F10</kbd> for UEFI/bios settings

You can delete the /efi/ubuntu folder in the ESP - efi system partition. Do not delete any other folders as they are essential.
You may need to copy /efi/Microsoft/Boot/bootmgfw.efi  to /efi/Boot/bootx64.efi
That is a backup or drive boot entry. Typically it is the Windows file, but grub makes it a copy of shimx64.efi. You can check sizes to confirm if you need to copy or not.
You may be able to use efibootmgr to remove ubuntu entry in UEFI. Line 132
Boot0001* ubuntu    

See man efibootmgr
sudo efibootmgr -b 0001 -B

But some efibootmgr commands do not work on HPs.

---

### Post by carlossuated on 2024-09-06
How would I delete directories from within the Grub CLI? I don’t think there is a way of writing or deleting files on it

---

### Post by oldfred on 2024-09-06
You have to use live installer or Windows.

---

