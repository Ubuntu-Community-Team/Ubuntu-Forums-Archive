---
title: "Ubuntu 14.04 boot issues on Toshiba Satellite NB15t-A1302"
date: 2014-12-25
forum: Installation &amp; Upgrades
---

### Post by lynn5 on 2014-12-25
I'm not trying to duel boot. I accidentally deleted Windows 8 preinstall  and I can't recover it nor can I afford the product. I want to use  Ubuntu 14.04 and have it currently installed however, every time I go to  boot it, it says: detecting media device, no media detected; then to insert a bootable  device and press the proper key. I reinstalled Ubuntu multiple times. At first it would show that it downloaded and it'd work perfectly until I restarted or shut it down. How do I get Ubuntu 14.04 to boot on my Toshiba Satellite  NB15t-A1302 laptop? This is also my first attempt at this so please  make it detailed and easy to understand.

---

### Post by Bucky Ball on 2014-12-25
*Thread moved to **Installation & Upgrades**.*

How are you trying to install it? Did you download the ISO and create an install USB/DVD and then boot from that and install?

---

### Post by oldfred on 2014-12-26
We need details, you install Boot-Repair into live installer:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some are also able to boot with Supergrub. Then repairs from inside working system are a bit easier.
 Toshiba Satellite supergrub to boot to fix things
[http://ubuntuforums.org/showthread.php?t=2240884](http://ubuntuforums.org/showthread.php?t=2240884)
But Supergrub may only work with BIOS install. I have not tried it with UEFI nor Rescatux with mentions UEFI.

 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

 Toshiba now seems to be like others and you need to copy grub into a /EFI/Boot folder, if UEFI install. Not sure it that already exists or not so we can give detailed commands after you post link to summary report.

There also may be some UEFI settings required, but you should have turned off secure boot and any fast boot in UEFI already.

You may want to check with Toshiba. Some vendors may ship you the Windows recovery set of DVD for a nominal shipping charge. Then if later you want to sell system, you can install Windows. Not may would want to buy a laptop without Windows.

---

