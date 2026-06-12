---
title: "install ubuntu dual boot windows 10"
date: 2022-05-03
forum: Installation &amp; Upgrades
---

### Post by farbodkain on 2022-05-03
hi

I tried to install ubuntu 20 beside my os windows 10, but for any reason after selecting "Ubuntu" on the boot menu everything become black and nothing happened at all. I created bootable on my USB flash with Rufus.

Thanks in advance

---

### Post by yancek on 2022-05-03
Are you selecting Ubuntu from the BIOS firmware of the computer or from  a Grub menu?  Since there are numerous reason for a computer failing to boot we will need more detailed information in order for a member to help.  I would suggest you go to the boot repair site at the link below while booted from your Ubuntu USB, download and run boot-repair using the 2nd option described on that page and select to Create BootInfo Summary.  When it finishes, it will give you a link which you should post here so members can view it and try to help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cigtoxdoc on 2022-05-04
I have been running dual-boot Windows 10 -- Ubuntu for years.  I put all my data files (documents, spreadsheets, etc.) in a partition formatted such as FAT32 or EXFAT so I can get the files from both Win and Ubuntu.  Just put in your usb stick loaded with the Ubuntu ISO and reboot with your boot set to read the usb before the hard drive and Ubuntu shoould carve out a space on your hard drive for itself.  Make sure you have an USB stick with the boot-repair ISO to get yourself out of trouble if Grub isn't installed properly.

John

---

### Post by grahammechanical on 2022-05-04
Please supply us information about your hardware. Make and model, CPU, memory, storage drives and video adapter.

I am assuming that "boot menu" means the UEFI settings boot menu. You must make sure that the Ubuntu installer USB memory stick is loaded in UEFI mode and not BIOS/Legacy/CSM mode. Otherwise when you do get Ubuntu installed you will have difficulty dual boot with Windows 10.

As to your problem we need to know about your computer hardware. 

Regards

---

