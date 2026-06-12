---
title: "Samsung UEFI Laptop won't boot from Live USB (Preinstalled with Windows 8)"
date: 2013-06-18
forum: Installation &amp; Upgrades
---

### Post by becksftw on 2013-06-18
I have a Saumsung 5 Ultrabook preinstalled with Windows 8, and am looking to do away with Windows completely, and install Ubuntu (So far I've been trying with 13.04 64bit). I made my LiveUSB using LiLi, disabled secure boot, disabled fast startup, enabled booting from CSM (I tried the UEFI and CSM option as well as CSM only), and changed the boot priority to go to my USB first. There where however 3 options, usb hdd, usb fdd, and usb cd. I didn't know which one to pick, so I put them all above the windows boot priority. Despite all of this it always boots up windows. The green light does however flicker on my usb when it boots, it that helps at all. I'm at a loss on what to do here, I've tried following everything I can find online. Does anyone have any suggestions?

---

### Post by fantab on 2013-06-19
I think you must choose 'USB HDD' to boot from USB.

Have you checked the integrity of your downloaded .iso with [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM")? Also, can you confirm that the .iso has burned correctly to the USB. 
If its a bad download then download Ubuntu.iso again. 
If its a bad burn then burn the .iso to the USB again as instructed:[ http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")

Boot Ubuntu in UEFI mode. Ubuntu installer does this automatically if it finds UEFI enabled. With UEFI you will get a black screen with options, with non-Uefi you will get the regular Ubuntu purple.

---

### Post by oldfred on 2013-06-20
With some systems it is not even USB-HD but under hard drives and then the USB flash drive appears as another hard drive. Not sure why the difference, but flash drives seem to be more as another hard drive.

---

