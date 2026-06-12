---
title: "Ubuntu overwrote my bootloader on wrong partition."
date: 2013-09-07
forum: Installation &amp; Upgrades
---

### Post by jarvinen-antti on 2013-09-07
I had my windows 8 running on a striped raid-array and windows 7 running on a usb drive (both had separate bootloaders). I started installing ubuntu 13.04 to the usb drive so it would replace my Windows 7 installation.

From the installation menu I selected replace my Windows 7 with Ubuntu and on the next screen I selected the correct drive where to install. During installation Ubuntu said it couldn't install bootloader correctly and prompted me to select another device. Well I selected again the USB drive where my windows 7 installation was and the instalation continued. After the installation the computer started to boot from the raid array which should have had the Windows 8 bootloader, but instead is was overwritten with ubuntu's bootloader and the loader wasn't even able to ubuntu from the USB drive. So I rebooted my computer to boot from the USB drive and it did and ubuntu is working from there.

How do I fix my Windows 8 bootloader on the raid array and why did Ubuntu overwrite it? I clearly selected the USB device where to replace my windows 7 installation and it went ahead and ****ed up my Windows 8 bootloader on another dirve :(

---

### Post by oldfred on 2013-09-07
Did you use Something Else or manual install, otherwise grub auto defaults to install to sda.

We need to see details. But do not run auto repair as that just installs grub everywhere so you can boot. You can uncheck auto repair but check update MBR and then in advanced boot choose which system to install to which MBR. Not sure about RAID.
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

