---
title: "Dual-Boot Ubuntu Win 10"
date: 2019-01-09
forum: Installation &amp; Upgrades
---

### Post by whitkim0923 on 2019-01-09
Good Day,
I I have SSD(256GB) on my Asus laptop for school. Partitioned part of it to install Ubuntu. Created a boot usb drive using Unetbootin for Ubuntu 16.04 Live x64.

Every time I restart my computer and tell it to boot from newly created usb, it just hangs on the purple splash page. 

I have used a couple different usb sticks to verify one wasn't damaged or corrupt. I used a couple different software creators for creating bootable usb and also have ensured my win 10 secure boot feature was disabled. In the menu that asks to either "try" , "install" or "check" the usb media. I have verified that it was working perfectly. 

Besides this I am lost and utterly frustrated. I know a lot of people suggest certain command line codes to fix issues but if I can't even get past splash page I can't do anything.

I do have pictures but don't see a way to upload.

Thank you,

---

### Post by oldfred on 2019-01-09
What model Asus?
What video card/chip? If nVidia you will need nomodeset boot parameter.
UEFI or BIOS install. Be sure to boot in same boot mode UEFI or BIOS as Windows is installed.

If newer system, better to use 18.04 as it includes more updates and is also a LTS or long term support version.
Have you updated UEFI from Asus and firmware for SSD? Most systems need that first.

---

