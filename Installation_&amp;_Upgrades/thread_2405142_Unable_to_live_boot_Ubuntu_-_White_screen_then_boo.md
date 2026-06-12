---
title: "Unable to live boot Ubuntu - White screen then boots to Windows"
date: 2018-11-01
forum: Installation &amp; Upgrades
---

### Post by thun0r on 2018-11-01
Hi, 

This is my first time trying to dual boot Linux with Windows 10. I have bought a second hand Thinkpad X220 (i5 4gb RAM 320HDD) which came with a clean install of Windows 10.

I've created a bootable USB drive with Universal-USB-Installer-1.9.8.3 and loaded ubuntu-18.04.1-desktop-amd64 into it.

Fastboot is off in Windows and I shrunk the C drive to half to allow room to install Ubuntu.

I then restart the laptop and F12 into the boot options, I select my USB drive with Ubuntu on it and it loads to the splash screen OK. 

However whenever I select try Ubuntu to load the live version the screen flicks to white then after a few seconds it boots to Windows as normal!?

I've tried 3 different pen drives both USB 2.0 and 3.0 with no luck.

In the BIOS options I have UEFI Legacy Boot mode Both with Legacy first which is default.

Any help would be much appreciated to get Linux working as I would like to move away from Windows.

Thank you

---

### Post by thun0r on 2018-11-02
Any help would be great?

---

### Post by yancek on 2018-11-02
Try adding the "nomodeset" option to the kernel line on boot.  When you see the menu, hit the e key on the keyboard to be able to edit by using the keyboard arrows to get to the beginning of the line beginning with the word linux, then arrow to the right and add nomodeset at the end or replace quiet splash-- with  nomodeset.

If you have windows 10, you most likely have an EFI install so I would suggest you read the Ubuntu documentation on dual booting with windows in EFI mode at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Did you verify the download by checking the md5sum or shasum?

---

