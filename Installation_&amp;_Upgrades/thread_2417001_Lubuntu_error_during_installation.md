---
title: "Lubuntu error during installation"
date: 2019-04-19
forum: Installation &amp; Upgrades
---

### Post by mikaelrask on 2019-04-19
i believe there is a bug in the installation of lubuntu 19.04 i have tried it twice and get the same error about boost.python error in job "bootloader" have tried to google and the only solution i have not tried the install without and internet connection.

have a nice day and hi from sweden.

---

### Post by cruzer001 on 2019-04-19
Did you checksum your iso download?

The "Alternate" installer is also a good option if you care to go with 18o4.

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

and hello from the states

---

### Post by mikaelrask on 2019-04-19
hi, i have downloaded a new copy of the iso and checksum it, it come out as clean is burning it to the usb and will try the installation again i be back with en update on my progress. 
ps i totally forgot to checksum the old iso but i have learned something today to always check my isos before :D

---

### Post by mikaelrask on 2019-04-19
im sorry to say that i got the same error this time during the installation 
 the error is the code below
Boost.Python error in job "bootloader".

 Command 'grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --force' returned non-zero exit status 1.
 Installing for x86_64-efi platform. Could not add entry to BootOrder: Invalid argument grub-install: error: efibootmgr failed to register the boot entry: No such device or address.
 
Traceback:

 [FONT=DejaVu Sans]File "/usr/lib/x86_64-linux-gnu/calamares/modules/bootloader/main.py", line 444, in run[/FONT] [FONT=DejaVu Sans]    prepare_bootloader(fw_type)[/FONT] 
[FONT=DejaVu Sans]  File "/usr/lib/x86_64-linux-gnu/calamares/modules/bootloader/main.py", line 411, in prepare_bootloader[/FONT] [FONT=DejaVu Sans]    install_grub(efi_directory, fw_type)[/FONT] 
[FONT=DejaVu Sans]  File "/usr/lib/x86_64-linux-gnu/calamares/modules/bootloader/main.py", line 285, in install_grub[/FONT] [FONT=DejaVu Sans]    "--force"])[/FONT] 
[FONT=DejaVu Sans]  File "<string>", line 6, in <module>[/FONT]

---

### Post by mikaelrask on 2019-04-19
i go back to the 18.04 release for now, but will follow the progress and see if there will be a fix for this :D thanks crusher0001 for helping me and have a good day/night/evening or what ever the time is at your place and ester.

---

