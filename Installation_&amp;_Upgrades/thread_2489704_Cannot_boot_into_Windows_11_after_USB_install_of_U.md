---
title: "Cannot boot into Windows 11 after USB install of Ubuntu 22.04"
date: 2023-08-07
forum: Installation &amp; Upgrades
---

### Post by frankftb on 2023-08-07
Hi everyone,

I hope someone could help.  I was installing Ubuntu 22.04 into a USB SSD, I would like to have a variety of OS on this drive.  When I was starting with Ubuntu 22.04, I forgot to go to Gparted and uncheck the boot and esp flags on my efi partition.  Now I have a dual boot system with Ubuntu and Windows 11.  The only way to have my computer boot to Windows 11 is by hooking up the SSD for dual boot, if the SSD is not there error occurs and it's unable to run Windows 11.  I would like to undo this and have my computer to boot to Windows 11 without the SSD, I did fdisk, and when I tried bootrec /FixBoot I was denied access to the boot partition. There are other articles that mention formatting the boot partition and recreating it. I want to see if there is a way that I could use Boot-Repair to do this and fix my issue.  I have pasted the log  here [https://paste.ubuntu.com/p/wBZ2hmhCvG/](https://paste.ubuntu.com/p/wBZ2hmhCvG/)

Thank you for your time and help.

Frank.

---

### Post by oldfred on 2023-08-07
You show bitlocker on.
Grub will only boot working Windows. But you should be able to directly boot Windows from UEFI boot menu, often f12, but varies by vendor. Same key/menu you used to select to install Ubuntu using live installer.

Is sda an internal or external drive?
Ubuntu using Ubiquity installer 22.04 & older, only installs grub to first drive. Whatever UEFI defines as first drive.
Newer versions of Ubuntu have Subiquity installer & other official flavors use other installers, also, those may let you choose which drive's ESP to use.

Various work arounds for Ubiquity posted:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

---

### Post by frankftb on 2023-08-08
sda is external usb SSD 250GB, I can boot to Windows thru Grub menu, I had to use the bitlocker key to do it.

---

### Post by frankftb on 2023-08-08
When I boot the laptop without the USB SSD attached, I get this :
GNU GRUB version 2.06
Minimal BASH-like line editing is supported......
grub>

---

### Post by tea for one on 2023-08-08
> **frankftb said:**
>  The only way to have my computer boot to Windows 11 is by hooking up the SSD for dual boot, if the SSD is not there error occurs and it's unable to run Windows 11.  I would like to undo this and have my computer to boot to Windows 11 without the SSD, I did fdisk, and when I tried bootrec /FixBoot I was denied access to the boot partition. There are other articles that mention formatting the boot partition and recreating it. I want to see if there is a way that I could use Boot-Repair to do this and fix my issue.
Boot-repair is not designed to repair Windows Boot Manager
Boot into Windows 11 with the SSD attached
Safely remove the SSD
Investigate Windows trouble-shooting tools

Alternatively, there are many useful websites e.g.
[https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/windows-boot-issues-troubleshooting](https://learn.microsoft.com/en-us/troubleshoot/windows-client/performance/windows-boot-issues-troubleshooting)

Also, the Windows 11 installation iso has an option for repair.

---

### Post by yancek on 2023-08-08
You should be able to change the boot priority to windows boot manager by accessing the BIOS firmware.  You may also be able to do it with efibootmgr from Ubuntu.  How to do that is explained at the link below.

 [https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

You have a vfat partition on the external drive so using the Ubuntu live USB, open GParted and highlight the vfat partition on the external drive by clicking on it in the main window, then click the partition tab at the top of the window and mouse down to Manage Flags and click and check the boxes next to boot and esp and apply the changes.  Then copy the ubuntu directory from the EFI partition on the windows drive to the EFI partition on the Ubuntu drive.  You will also need to change the entry for /boot/efi in the /etc/fstab file and put the correct UUID there.  You can get that with the blkid command.

---

### Post by frankftb on 2023-08-08
Hi guys, thank you for your help.  I am trying the efibootmgr first, yancek when you say copy the ubuntu directory from the EFI partition on the windows drive to the EFI partition on the Ubuntu drive, I go to /EFI/ubuntu on my computer's internal drive nvme0n1p1 where i find BOOTX64.CSV grub.cfg grubx64.efi mmx64.efi and shimx64.efi, but on /dev/sda1 which is my ssd partition1 where fat32 boot,esp is located i only see $RECYCLE.BIN and System Volume Information directories, I don's see an EFI directory.

Thanks again for your help.

---

### Post by yancek on 2023-08-09
Mount sda1:  sudo mount /dev/sda1 /mnt
sudo mkdir /mnt/EFI(use upper case letters for EFI)
sudo mkdir /mnt/ubuntu (make sure you use lower case letters for ubuntu)

Then while booted into Ubuntu make sure you can access /boot/efi on the nvme drive.  Mount if necesary and simply copy the the ubuntu directory ubuntu from within that directory.  You would need to change directories to /boot/efi/EFI first then:  sudo cp ubuntu/* /mnt/EFI
You will need to check the entry for /boot/efi to make sure the UUID is correct for the partition on the Ubuntu drive.

---

