---
title: "Cannot boot after updating to Kubuntu 17.04"
date: 2017-04-17
forum: Installation &amp; Upgrades
---

### Post by onuralparslan on 2017-04-17
I have a dual boot Kubuntu and windows. I updated Kubuntu version 17.04 from 16.10. After updating, I cannot enter Kubuntu. It gives the following error during boot:

Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load image \EFI\BOOT\grubx64.efi: Not Found
start_image() returned Not Found

I tried Boot-Repair, but it still gives the same error.  The result of Boot-Repair is at [http://paste2.org/4cVxxVd6](http://paste2.org/4cVxxVd6) . Did the update delete my EFI partition? How can I fix it?

---

### Post by RobGoss on 2017-04-17
From looking and the boot summary it looks as tho the Grub is not Installed on the **MBR** partition, try running the boot repair again and this time when installing the Grub loader choose the **sda** partition were the master boot record should always be installed when dual booting Windows and Linux

---

### Post by onuralparslan on 2017-04-17
I installed windows and linux as GPT. I have always booted from GPT. There may be extra mbr data on the drive, but it was not used.
When I tried boot-repair, "separate boot partiton" was selected and it was set to sda (there were no other options)

---

