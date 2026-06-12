---
title: "Unable to create a bootable USB disk of Ubuntu"
date: 2019-08-15
forum: Installation &amp; Upgrades
---

### Post by sunrise718 on 2019-08-15
I am trying to create a bootable USB disk of Ubuntu desktop.  I have the ISO file on the USB drive.  

However, the Ubuntu software that creates bootable drives generates an error message when I click to create the bootable drive.  

It asks for the admin password.  When I enter the admin password, it tells me that it cannot generate the boot drive.

Now what?  How can I give it the correct permission to accomplish what should be a simple task?

---

### Post by Autodave on 2019-08-16
You will not be to create a bootable USB drive if the file is on the same drive.  It must be on a different drive because the drive being used for the creation of the bootable .iso will be wiped clean first.

---

### Post by C.S.Cameron on 2019-08-16
You can install Ubuntu on the drive it was booted from: [https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from](https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from)

However if your computer boots UEFI just extract the ISO to the USB drive using 7Zip or similar.

You can boot an ISO directly by loop mounting, but need to have grub installed to do so.

---

### Post by sunrise718 on 2019-08-17
> **Autodave said:**
> You will not be to create a bootable USB drive if the file is on the same drive.  It must be on a different drive because the drive being used for the creation of the bootable .iso will be wiped clean first.

Thank you, Autodave.  I created the bootable USB drive with a blank USB and it worked like a charm.  I was able to install Ubuntu and all is well.

---

### Post by sunrise718 on 2019-08-17
> **C.S.Cameron said:**
> You can install Ubuntu on the drive it was booted from: [https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from](https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from)

However if your computer boots UEFI just extract the ISO to the USB drive using 7Zip or similar.

You can boot an ISO directly by loop mounting, but need to have grub installed to do so.

Thanks, C.S.Cameron!  I followed AutoDave's advice and it worked.  I don't have Grub and that seemed too complicated.

---

