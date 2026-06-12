---
title: "cannot boot usb stick in Acer D17ES Aspire TC-1660"
date: 2022-01-12
forum: Installation &amp; Upgrades
---

### Post by Richard-S on 2022-01-12
I have not been able to change the BIOS in this new box so that the Ubuntu stick will boot. My older Aspire had a UEFI BIOS but I could change boot modes to legacy boot. This new BIOS does not appear to have legacy boot listed as an option.

Should I send this new box back to Amazon for a refund and buy something else+

Richard

---

### Post by yancek on 2022-01-12
Some newer Acer machines require that a Supervisor Password be set in the BIOS and Trust be enabled before one can install another OS.  You might check your manual orsee if you can find it online.  Have you tested the usb on another computer to see  if it boots.  What software did you use to make the usb bootable.  What is a "USFI" BIOS?

---

### Post by oldfred on 2022-01-12
Some also require control-S to get more options.
Most tools to create Ubuntu live installer flash drive, create one that is both BIOS & UEFI.
All pre-installed Windows systems since 2012 have been UEFI with gpt partitioning. And Ubuntu has worked with almost all those systems.

Many Acer, even new require UEFI update and if SSD, SSD firmware update.
You need to change drive(s) from RAID or Intel RST to AHCI in UEFI settings.
If dual booting with Windows you need to install AHCI drivers first & turn off fast start up.

Most Acer are similar, some differences if Intel or AMD. And if nVidia driver required.
Acer Inspire XC 1660G Can't install
[https://ubuntuforums.org/showthread.php?t=2468820](https://ubuntuforums.org/showthread.php?t=2468820)
Acer Aspire 5 Model A515-54-5649  Intel Core i5-10210U Install Tutorial
[https://ubuntuforums.org/showthread.php?t=2437702](https://ubuntuforums.org/showthread.php?t=2437702)
Acer Swift 5 (2019) ctrl-s  in UEFI required to be able to change to AHCI mode.
[https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown](https://askubuntu.com/questions/1217061/installation-on-acer-swift-5-freezes-no-partitions-shown)
acer predator helios 300 PH 315-51 i5 8th gen nouveau.modeset=0
[https://askubuntu.com/questions/1118751/has-anyone-successfully-dual-booted-ubuntu-18-04-lts-on-their-acer-predator-heli](https://askubuntu.com/questions/1118751/has-anyone-successfully-dual-booted-ubuntu-18-04-lts-on-their-acer-predator-heli)

---

### Post by Richard-S on 2022-01-13
I read the above posts and links, and then, using MKUSB, I made anotherUbunto USB stick, with a UEFI partition this time, which the other one did not have. It booted right up.

Thank you for your assistance.

Richard.

---

