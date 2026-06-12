---
title: "Cannot install on flash drive: partitions cannot be created"
date: 2017-09-10
forum: Installation &amp; Upgrades
---

### Post by onlineguy on 2017-09-10
Hi,

I want to create a permanent Ubuntu installation (either 16.04 or 17.04) on a flash drive. I will only use this flash drive with one specific laptop (HP Elitebook 840 G4) that runs Windows 10 in UEFI mode. I have problems creating the necessary partitions during the installation process. After making manual adjustments I always get an error telling that swap partition (or efi if I choose not to create a swap partition etc...) could not be created and I am returned to the previous screen. These are the partitions I would like to setup:

sda1: efi
sda2: root
sda3: home
sda4: swap

Any ideas what the problem might be or how to find the cause?

---

### Post by BenginM on 2017-09-10
Hiya, I believe you need to create the partitions only on sda , if that's your first/main SS/HD .

Wait, you want to install Ubuntu on a flash drive ? and not on an internal SSD or HDD  ! if that's the case, then am not sure why would you want to do that...
 you need to select the external drive and create the partitions there.

the above partitions you created are on different drives which is wrong , they must be all created on the same internal/external drive .

---

### Post by echotech2 on 2017-09-10
Shouldn't the partitions be sd*x*(parttions) where x=flashdrive  e.g. sda1, sda2, etc.?

---

### Post by oldfred on 2017-09-10
With UEFI full install to flash drive or any external drive you will have to manually copy /EFI/ubuntu from sda to external drive twice. Second time copy to /EFI/Boot and rename shimx64.efi to bootx64.efi. And then edit fstab will correct UUID for external drive.

Issue is Ubuntu's grub only installs to ESP - efi system partition seen as sda, no matter what you say in installer.
And UEFI only boots from /EFI/Boot/bootx64.efi on ESP on external drive.
You can manually install grub in correct mode, but have to manually create & update grub.cfg as not then part of install.

See also:
 Full install
[https://askubuntu.com/questions/906857/installing-ubuntu-on-usb-and-booting-from-destop-with-uefi](https://askubuntu.com/questions/906857/installing-ubuntu-on-usb-and-booting-from-destop-with-uefi)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks) 

      
 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad

---

### Post by sudodus on 2017-09-10
There are two alternatives to install into a USB flash drive or a memory card (with flash memory cells) or an SSD connected via USB. (If an SSD is connected internally, you can use the standard procedure, the same as for a hard disk drive.)

1. The easy alternative would be to create a persistent live drive. See these links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

2. A more complicated alternative (but better in some ways) is to install a system like installed into an internal drive (but to this external drive). This is described in a detailed way for another but I think similar case at this link

[Boot Ubuntu from external drive.](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

A crucial point that makes things easier is to disconnect and/or uplug the internal drive before the installation (and plug it back afterwards).

---

### Post by onlineguy on 2017-09-10
Sorry, I made a typo in my first post. All partitions ARE actually on the same drive (sda1, sda2 etc...), I will fix my first post. Just believe me, I really need a permanent install on an external flash drive / USB stick. In case I was unclear about that: after defining my partition setup in ubiquity I get the error message, so no partition is actually created. I cannot copy anything to /etc or other places since the actual installation never takes place.

So, thanks oldfred and others, I will check the links.

---

