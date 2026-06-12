---
title: "System BootOrder not found"
date: 2020-08-18
forum: Installation &amp; Upgrades
---

### Post by stuartschady on 2020-08-18
I recently installed Ubuntu 20.04 for the first time on my Toshiba Satellite.

Now everytime I restart the computer I get a message:

"System BootOrder not found. Initializing defaults.
Creating boot entry "BootXXXX" with label "ubuntu" for file "\EFI\ubuntu\shimx64.efi

And then Ubuntu loads up. It seems to be creating unncessary BootXXXX files which I can see if I run efibootmgr in the terminal.

This seems to have come up a few times before: [https://askubuntu.com/questions/1042747/system-bootorder-not-found?noredirect=1&lq=1](https://askubuntu.com/questions/1042747/system-bootorder-not-found?noredirect=1&lq=1)
I do not have many of the options in my BIOS that are suggested for the fix. 

Does any one know a way to resolve this from within Ubuntu using the efibootmgr? 

Thanks

---

### Post by oldfred on 2020-08-18
With Acer you have to set a UEFI password with Secure boot on. That opens more settings.
Not seen that with Toshiba, but you need to review manual to see what settings you have.

You also may need to update UEFI to latest version available.

---

### Post by stuartschady on 2020-08-19
For anyone who experiences this issue and has similar Bios issues to me  (not allowing for custom boot options), this seems to have solved the  issue:

Go to terminal:
$ sudo su
# cd /boot/efi/EFI
# mv BOOT BOOT_back
# cp -R ubuntu BOOT
# cd BOOT
# mv shimx64.efi bootx64.efi

I found this on some other forums. Basically you are replacing your boot folder with the contents of the ubuntu folder.
I do not understand enough about Ubuntu/Linux distros to understand why this works, but it has solved the issue.

---

### Post by oldfred on 2020-08-19
Ubuntu should be putting a copy of shimx64.efi as /EFI/Boot/bootx64.efi.
That is the fallback boot entry for internal drives and the default boot entry for all UEFI external drives.

Perhaps new grub needs all the files in /EFI/Boot. Before you did have to have all the boot files in /EFI/ubuntu even if booting with /EFI/Boot/bootx64.efi?

---

### Post by cno2 on 2021-03-21
Thanks! This worked for me on a HP Elitebook Folio 9470m. A recent update of Ubuntu LTS did hide the boot options.

---

### Post by fernmark on 2021-06-18
Thanks! This worked on a lenovo v570 with no bios efi management capability.

---

