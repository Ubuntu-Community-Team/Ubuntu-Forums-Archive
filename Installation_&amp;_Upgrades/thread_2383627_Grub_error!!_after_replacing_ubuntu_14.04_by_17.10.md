---
title: "Grub error!! after replacing ubuntu 14.04 by 17.10"
date: 2018-01-27
forum: Installation &amp; Upgrades
---

### Post by tounsimed on 2018-01-27
Hello, I install ubuntu 17.10 in place of ubuntu 14.04. Everything was ok. *In *the end of installation the system ask me to restart, when I restart I get this message:
error: file "/boot/grub/x86_64_efi/normal.mod" not found
and I cannot boot linux nor windows 8
I use a live ubuntu usb and I get the following Boot info 

[https://paste.ubuntu.com/26472537/](https://paste.ubuntu.com/26472537/)

Thank you

---

### Post by managerceo1 on 2018-01-27
From the liveDVD -> "try ubuntu" mode -> desktop -> key combo ctl+alt+t to get a terminal interface.
In this terminal execute the terminal commands:


Code:
sudo fdisk -lu
sudo parted -l

---

### Post by oldfred on 2018-01-27
@managerceo1
Partition info is in Boot-Repair's summary report OP posted link to.

You have an UEFI system.
But show grub installed for both UEFI boot and BIOS boot.
And fstab does not show mount of ESP - efi system partition, so new install looks like it was in BIOS boot mode and then old install was UEFI.
And now if you try to boot in UEFI mode that grub is the old version.

Use Boot-Repair booted in UEFI mode, and a full uninstall and reinstall of grub2. So you uninstall the BIOS boot version of grub and install the UEFI version of grub.
And always boot system in UEFI mode.

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by tounsimed on 2018-01-27
Thank you
It works now, but it does not look very pretty,
maybe I missed a step

[IMG]https://lh3.googleusercontent.com/F_Ixa59mv_ogY_FKN02KYy_6quNEhVVZe1duaWc5ZkBEylXNIwL1fYjlBUVlC6pMh8lNFAykCprgieDicDQ_=w1920-h952[/IMG]

---

### Post by oldfred on 2018-01-28
Grub is typically not "pretty". But I set mine for 3 sec, so almost do not see it.

You can add background and colors.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays) 

Or since UEFI you can use the rEFInd boot manager (you still use grub to boot).
      
 [http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

