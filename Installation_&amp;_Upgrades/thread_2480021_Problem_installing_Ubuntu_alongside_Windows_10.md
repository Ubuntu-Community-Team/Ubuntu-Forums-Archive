---
title: "Problem installing Ubuntu alongside Windows 10"
date: 2022-10-16
forum: Installation &amp; Upgrades
---

### Post by alea78 on 2022-10-16
I have an old laptop which had Centos on it and wanted to have a dual boot feature so installed Windows 10 in its place. I used the partitioning tool in Windows 10 to split the hard drive into two partitions. I downloaded Ubuntu, flashed it onto a USB stick and installed it on the second partition, selecting the option "install alongside Windows". Unfortunately the dual boot feature does not work, the laptop always boots into Windows and does not bring up the GRUB menu. I tried installing a third party bootloader on Windows which is GRUB2 and tried to set that up so it pointed at Windows and Linux but that doesn't work either (same thing). How do I get Ubuntu and the bootloader installed so that I get the option on startup to choose which operating system to boot into? Bear in mind that I currently have no way of booting into Ubuntu. Is there something I need to do in the BIOS?

---

### Post by yancek on 2022-10-16
Is your computer EFI capable?  Do you have the OS installed on a GPT drive?  If windows is installed UEFI, then Ubuntu will need to be UEFI or it won't boot windows.  Did you access the BIOS firmware to set Ubuntu first in boot priority?

---

### Post by alea78 on 2022-10-16
I do not know if it is EFI capable. No I don't have the OS installed on a GPT drive and windows is not installed UEFI. The laptop has BIOS, I don't know what UEFI is. There is no option in the BIOS to set Ubuntu to boot first, the only options I have are OS boot manager, USB or CD/DVD ROM.

---

### Post by zebra2 on 2022-10-17
For a Bios (non efi) install.
You will need a 8MB bios boot partition as your first partition.
You will need a 256MB ESP partition. (even for a bios boot)
You wil need a NTFS partition for Windows 10 with the boot flag enabled.
You will heed a EXT4 partition for Ubuntu.
Install Windows 10 first and turn off "sleep  mode" in the power settings. The Grub boot app cannot boot a sleeping partition. 
Then boot your Ubuntu Startup disk or USB and install Ubuntu on the EXT4 partition. 

All of these partitions can be created with the Ubuntu start up disk if you choose install and then the (other) selection which will get you to the partitioner. 
You won't have to format the bios boot partition or the esp partition because the installer will format them for you. But you will have to check off to format the NTFS and EXT4 partitions. 
This is all a pretty easy process once you have done it a few times.

Note: the installation will fail if you don't have a bios boot and esp partition. The fact that it is a bios install makes no difference starting with 22.04.

---

### Post by alea78 on 2022-10-17
Thanks, I'll give that a try and let you know how I get on.

Dual booting seemed to be a lot simpler when I did it 25 years ago.

---

### Post by yancek on 2022-10-17
> I tried installing a third party bootloader on Windows which is GRUB2 

I don't know what that means, from your first post.  Grub2 has been the default boot loader on Ubuntu for 13 years.  What 3rd party boot loader are you referring to?  You should not install Grub2 to a windows partition which seems to be what you did per your first post..  If you accepted the defaults during the installation of the bootloader, it should have installed Grub code in the MBR and created an entry for windows.

---

### Post by alea78 on 2022-10-17
> **zebra2 said:**
> For a Bios (non efi) install.
You will need a 8MB bios boot partition as your first partition.
You will need a 256MB ESP partition. (even for a bios boot)
You wil need a NTFS partition for Windows 10 with the boot flag enabled.
You will heed a EXT4 partition for Ubuntu.
Install Windows 10 first and turn off "sleep  mode" in the power settings. The Grub boot app cannot boot a sleeping partition. 
Then boot your Ubuntu Startup disk or USB and install Ubuntu on the EXT4 partition. 

All of these partitions can be created with the Ubuntu start up disk if you choose install and then the (other) selection which will get you to the partitioner. 
You won't have to format the bios boot partition or the esp partition because the installer will format them for you. But you will have to check off to format the NTFS and EXT4 partitions. 
This is all a pretty easy process once you have done it a few times.

Note: the installation will fail if you don't have a bios boot and esp partition. The fact that it is a bios install makes no difference starting with 22.04.

I tried creating the partitions you suggested in Windows before installing Linux. I selected the partitions and formatted as you suggested. Same problem, it boots straight into Windows.

---

