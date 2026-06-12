---
title: "BootDevice Not Found - HP ProBook, Ubuntu 24.10 installation"
date: 2024-12-01
forum: Installation &amp; Upgrades
---

### Post by jt1324145 on 2024-12-01
[COLOR=#2A3C42][FONT=-apple-system]I installed Ubuntu 24.10 from a USB on my HP ProBook (I can see the installation on the hard drive when I boot again from the USB). However, I cannot boot into the new Ubuntu operating system from the hard drive. I went into the BIOS, and I tried the different UEFI and Legacy boot options. It still doesn't work. I can see my hard drive as a boot choice when I boot up, but when I select it, it says it cannot find the boot device. Any ideas?[/FONT][/COLOR]

---

### Post by yancek on 2024-12-01
Run the following command from the 'llive' usb and post it here:  sudo efibootmgr

You might need to get and run boot repair.  The link below explains it.  Use the 2nd option described on that page while booted from the 'live' usb.  Select the Create BootInfo Summary option and post the link you get when it finishes here so members can review it.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by jt1324145 on 2024-12-03
I ran the boot repair and the results are here. [COLOR=#131313][FONT=-apple-system]Getting the same error. [/FONT][/COLOR][https://paste.ubuntu.com/p/4WbHVsft7j/](https://paste.ubuntu.com/p/4WbHVsft7j/)

Any additional insight would be appreciated.

---

### Post by jt1324145 on 2024-12-03
I reset my boot security settings, and it is now working!

---

