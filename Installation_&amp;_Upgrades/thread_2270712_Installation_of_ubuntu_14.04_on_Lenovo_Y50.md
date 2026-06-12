---
title: "Installation of ubuntu 14.04 on Lenovo Y50"
date: 2015-03-25
forum: Installation &amp; Upgrades
---

### Post by a2l007 on 2015-03-25
Hi,
I have a Lenovo Y50  with 1TB HDD + 8GB SSD and Windows 8.1 pre installed. I'm trying to install ubuntu 14.04 via a live usb. I've gone through the following tutorial for getting it installed but hit some issues midway:
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

Since it wouldn't automatically load my live USB, i disabled UEFI Secure boot and switched to legacy boot. This worked in loading the live USB and in the installation process, i assigned partitions for swap as well as the root directory. But when i tried to proceed to the next step, i got a error message specifying that my system requires that I should be assigning a separate partition for boot .
What should i be doing here?  Also, as per the tutorial it is always recommended to install ubuntu under Secure boot. So, is there any way i can load the live usb via UEFI Secure boot?

Thanks in advance

---

### Post by albaniaguard on 2015-03-25
you can try install normaly and you have an opsion to try ubuntu,not with dualbot....

---

### Post by grahammechanical on 2015-03-25
I think that there is something that you need to understand.

When Windows 8.1 is pre-installed it is installed in EFI mode (not legacy mode). This means that Ubuntu has to be installed in EFI mode as well. The live session has to be run in EFI mode. So, switching from EFI to legacy mode was the wrong thing to do.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by a2l007 on 2015-03-25
But if i run in EFI mode, it is not picking up my live usb. What should i do to resolve that?

---

### Post by Vladlenin5000 on 2015-03-25
Every USB I used so far did UEFI perfectly. What software/method have you used to create yours?

---

### Post by a2l007 on 2015-03-26
Used the tool mentioned in the guide:
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
Wouldnt this do the trick?

---

### Post by Vladlenin5000 on 2015-03-26
Try Rufus - [https://rufus.akeo.ie/](https://rufus.akeo.ie/) - and select UEFI and GTP.

---

### Post by a2l007 on 2015-03-28
I tried doing it with Rufus as well but my live usb still wont boot in UEFI mode. Can someone please guide me regarding this?

---

### Post by a2l007 on 2015-03-30
Worked on this a little more and I was able to boot the usb by doing the following:
Press Shift while selecting Restart. In the settings menu that comes up, select UEFI Settings and Select EFI USB. This helped me to boot the live USB.

---

