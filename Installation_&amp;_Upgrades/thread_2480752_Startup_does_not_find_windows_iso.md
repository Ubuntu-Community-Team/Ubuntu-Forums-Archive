---
title: "Startup does not find windows iso"
date: 2022-11-08
forum: Installation &amp; Upgrades
---

### Post by Papi47 on 2022-11-08
22.04 will find and Ubuntu iso but it will not see the Windows10 iso that is right next to it.  How do I fix this?

---

### Post by QIII on 2022-11-08
Your question is difficult to understand.

Are you having difficulty finding the images in a file manager?

---

### Post by Papi47 on 2022-11-08
> **QIII said:**
> Your question is difficult to understand.

Are you having difficulty finding the images in a file manager?

No, the startup disk creator refuses to see the window iso.  I just read somewhere that it is just a cloning tool for Ubuntu only.  I'm trying to find something that will work

---

### Post by QIII on 2022-11-08
So, perhaps your title might better be "Startup Disk Creator does not find windows iso"?

Or even "How do I create Windows installation media from Ubuntu?"

---

### Post by oldfred on 2022-11-08
Best to use Windows tools.
Microsoft made one file, the .wim file over 4GB. That file then cannot be on a FAT32 partition which is required for UEFI boot.
Microsoft install creator tool splits the .wim file so it does fit.
Old versions of Windows with smaller .wim, could be just extracted to a FAT32 partition and boot in UEFI mode.

Create Windows installer with the oversize .wim file
[https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive](https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive)
[https://help.ubuntu.com/community/Installation/iso2usb/diy/windows-installer-for-big-files](https://help.ubuntu.com/community/Installation/iso2usb/diy/windows-installer-for-big-files)
[https://www.dedoimedo.com/computers/windows-10-usb-media-linux.html](https://www.dedoimedo.com/computers/windows-10-usb-media-linux.html)

---

### Post by Papi47 on 2022-11-08
> **oldfred said:**
> Best to use Windows tools.
Microsoft made one file, the .wim file over 4GB. That file then cannot be on a FAT32 partition which is required for UEFI boot.
Microsoft install creator tool splits the .wim file so it does fit.
Old versions of Windows with smaller .wim, could be just extracted to a FAT32 partition and boot in UEFI mode.

Create Windows installer with the oversize .wim file
[https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive](https://help.ubuntu.com/community/mkusb#Windows_USB_install_drive)
[https://help.ubuntu.com/community/Installation/iso2usb/diy/windows-installer-for-big-files](https://help.ubuntu.com/community/Installation/iso2usb/diy/windows-installer-for-big-files)
[https://www.dedoimedo.com/computers/windows-10-usb-media-linux.html](https://www.dedoimedo.com/computers/windows-10-usb-media-linux.html)


Thank you for the links I will check them out

---

