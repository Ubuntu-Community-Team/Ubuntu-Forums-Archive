---
title: "Ubuntu 18 install crashes when installing grub2"
date: 2019-08-20
forum: Installation &amp; Upgrades
---

### Post by juakofz on 2019-08-20
Hi,

I am trying to install Ubuntu 18 on my computer via an ubuntu live usb, in uefi mode. I originally was trying to install it alongside win10 but it kept failing, so I deleted everything but a small driver partition and tried again. I also should point out I am running the installer with the pci=noacpi option, or else it won't work at all.

I have a small SSD and a HDD. I created the following partitions:

SSD:
- EFI system partition
- ext4 / partition

HDD:
- swap partition
- ext4 /home partition
- small driver partition at the end of the drive

The installer does its thing, but when it reaches "Installing the 'grub2' package..." it freezes. I have waited for hours but it seems to have crashed. After restarting the computer, I goes directly into the BIOS.

I tried then using boot repair. It tried to install the grub2 package and... it also crashes the computer.

What causes the issue? How do I solve it?

Thank you very much for you help

---

### Post by yancek on 2019-08-20
Ubuntu has a site (link below) which explains dual booting with windows UEFI which would have been good to read before you began.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you have boot repair, rather than trying to repair, select the Create BootInfo Summary option and run that and post the link you get when it finishes.  That should give members some useful information and hopefully a suggested solution.

---

