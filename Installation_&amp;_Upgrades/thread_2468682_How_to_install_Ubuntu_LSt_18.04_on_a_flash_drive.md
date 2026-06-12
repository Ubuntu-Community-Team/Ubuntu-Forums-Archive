---
title: "How to install Ubuntu LSt 18.04 on a flash drive"
date: 2021-11-08
forum: Installation &amp; Upgrades
---

### Post by mario27 on 2021-11-08
Hi

I wish to install Ubuntu LST 18.04 on a USB flash drive (attached to a Fedora 33 machine).
I am looking at [https://linuxhint.com/install_an_entire_ubuntu_on_a_usb_flash_drive/](https://linuxhint.com/install_an_entire_ubuntu_on_a_usb_flash_drive/)

Just before to install, I get the following msg:

----------------
> If you continue, the changes listed below will be written to the disks. Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI4 (0,0,0) (sdc)

The following partitions are going to be formatted:
** LVM VG fedora, LV swap as swap **   
 partition #1 of SCSI4 (0,0,0) (sdc) as ext4
 partition #5 of SCSI4 (0,0,0) (sdc) as ext4
 partition #6 of SCSI4 (0,0,0) (sdc) as swap

-----------------

How is that ***LVM VG fedora, LV swap as swap** *is going to be formatted? Is that harmless? How do I avoid it?
(sdc is the USB flash drive, I have partioned it into /, /home, and swap.)
Thanks
m. 
[URL="https://linuxhint.com/install_an_entire_ubuntu_on_a_usb_flash_drive/"]
[/URL]

---

### Post by mIk3_08 on 2021-11-08
> **mario27 said:**
> Hi

I wish to install Ubuntu LST 18.04 on a USB flash drive (attached to a Fedora 33 machine).
I am looking at [https://linuxhint.com/install_an_entire_ubuntu_on_a_usb_flash_drive/](https://linuxhint.com/install_an_entire_ubuntu_on_a_usb_flash_drive/)
[URL="https://linuxhint.com/install_an_entire_ubuntu_on_a_usb_flash_drive/"]
[/URL]

We have some guides here for you to read. This guide might help you. Good Luck and Regards.
[HTML]https://help.ubuntu.com/community/Installation/FromUSBStick[/HTML]
[HTML]https://help.ubuntu.com/community/Installation/UEFI-and-BIOS[/HTML]
[HTML]https://wiki.ubuntu.com/CDROMUbuntuInstallationFromWindows[/HTML]
Or just Click Here [ Link#1]("https://help.ubuntu.com/community/Installation/FromUSBStick") [Link#2]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS") [Link#3]("https://wiki.ubuntu.com/CDROMUbuntuInstallationFromWindows")

---

### Post by tea for one on 2021-11-08
Your intention is not completely clear and further information is required.
There are three types of Ubuntu installations on USB devices:-

[LIST]
[*]Download an Ubuntu ISO and prepare installation media.
[*]Make an Ubuntu device with persistent storage (without user or password)
[*]Create a full Ubuntu installation on an external device including user and password
[/LIST]
Your pre-prepared partition scheme looks unusual.
The installer will take care of partitions unless you have very specific reasons to avoid this. 

If you are using Fedora, the software installation packages may not be familiar to Ubuntu forum members.

Finally, please take note of the info here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2021-11-08
Your link looks like a full install to a flash drive using a flash drive with the installer.
You should not see your LVM being modified, but whatever you had on flash drive would be. Did you have an LVM on flash drive?

Do you want a LVM install or standard partitions?
UEFI or BIOS install?
 Your link looks like a BIOS type install, but UEFI has some additional complications where you must partition in advance to have an ESP - efi system partition on external drive. 

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive. (I have not had that work, but others have.)
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

I also suggest using gpt partitioning whether BIOS or UEFI. But gpt needs the ESP for UEFI boot or a bios_grub partition for BIOS boot.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

