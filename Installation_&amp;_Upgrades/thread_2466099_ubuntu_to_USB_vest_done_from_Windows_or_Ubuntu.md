---
title: "ubuntu to USB vest done from Windows or Ubuntu?"
date: 2021-08-19
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2021-08-19
I have a dual OS laptop, running win10 and Ubuntu 20 (up-dated today),  I want to re-install Ubuntu, a fresh wipe so to speak.  What is easiest and best way?

---

### Post by grahammechanical on 2021-08-19
Are both operating systems working correctly? Unless you have a reason not to, then use Ubuntu to download ISO image and burn it to the USB memory stick.

[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview)

 Make a note of your Ubuntu partitions and use the Something Else option to install Ubuntu into the existing Linux partitions. If you set the installer to format the partitions then the new install of Ubuntu will overwrite everything on the Linux partitions.

If this laptop has UEFI motherboard then do not format the EFI boot partition as your will wipe out the Windows 10 boot loaders.

Have you never done an install of Ubuntu using the Something Else method? There are steps to take and precautions to keep. Installing Ubuntu only becomes easy when we have done 10 - 12 re-installs and that is the time we are most likely to make a mistake.

See section 6 Allocate drive space

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)


If you select the first option - Erase Disk and Install Ubuntu you will lose Windows 10. 

Regards

---

### Post by mawil10132 on 2021-08-19
I've been able to make a start usb with image, thank you

---

