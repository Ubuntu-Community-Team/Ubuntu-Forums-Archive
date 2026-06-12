---
title: "Boot repair didn't help"
date: 2013-08-19
forum: Installation &amp; Upgrades
---

### Post by leon6 on 2013-08-19
Hi, I installed Ubuntu 13.04 on my 64 bit machine that has Windows 8 using the amd64 version from a liveUSB. After installing, it still booted to Windows straight, so I followed the instructions here to use Boot Repair.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Once that was done, however, it still booted straight to windows. Can someone help? The paste url is paste.ubuntu.com/6004508

---

### Post by oldfred on 2013-08-19
It looks like you installed Ubuntu in CSM/BIOS/Legacy mode not UEFI. To dual boot with Windows which is in UEFI mode you must have Ubuntu in UEFI mode. And it looks like Boot-Repair converted install to UEFI mode by uninstalling grub-pc and installing grub-efi.

But you have to go into UEFI menu and choose to boot the ubuntu entry. The efi partition holds many boot loaders and you have to select which you want as default.

Also HPs have lots of efi files in efi partition and Boot-Repair adds them all to grub menu. You may or may not want all of them. Instructions on manually cleaning up menu are in the link in my signature.

---

### Post by leon6 on 2013-08-19
Thanks for the reply! I took a look at the link in your signature, but I'm a little confused...how do I get to the UEFI menu? And once I'm there, how do I ensure that I can choose to boot either Windows or Ubuntu?

EDIT: I tried it. Also, the reason that I installed in CSM mode was because when I tried to boot from my usb drive using UEFI, I just got a black screen. I did a little research and it apparently was an issue was graphics card or something like that. So, I enabled CSM, and chose the option to boot from usb without UEFI and I managed to follow the directions about nomodeset and stuff like that, and I installed Ubuntu. Now, in the boot menu, I can choose Ubuntu, and it takes me to the GRUB menu. I choose Ubuntu, but all I get is the black screen again...I have a Nvidia Geforce GT 740m, I wonder if that's the cause...

EDIT 2: I reread the instructions about nomodeset and accessing kernel options...that simply isn't an option when I instantly get a black screen when trying to boot it.

---

### Post by ubfan1 on 2013-08-19
At the grub menu, type e, and you can edit the linux line with the "quiet splash" and add the nomodeset.

---

### Post by oldfred on 2013-08-20
Grub seems to remember keystokes while grub is loading in the background. So just after BIOS press down arrow once and that should be the recovery mode boot menu item in grub menu.

---

