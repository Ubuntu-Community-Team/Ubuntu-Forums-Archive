---
title: "Install Ubuntu 18.04 on a 64gb Sandisk micro sd card"
date: 2019-04-01
forum: Installation &amp; Upgrades
---

### Post by aadarshram2003 on 2019-04-01
Hello,

I am an absolute beginner in installing Ubuntu. I want to install Ubuntu 18.04 LTS (newest version) on a 64GB Sandisk Micro Sd card. I want to achieve this, by using a live version of Ubuntu on another USB drive. I have searched various threads and I couldn't understand half of it. I am having a Lenovo Z50-70 laptop and I want to run ubuntu in a HP Pavillion with a ssd. Please help me in guiding with a step-by-step procedure.

---

### Post by C.S.Cameron on 2019-04-01
Unplug the internal drive, plug in the target SD card and boot the installer USB. Install to the SD card as you would to internal drive. 
See: [https://askubuntu.com/questions/446682/how-to-install-ubuntu-on-portable-external-hard-drive/1122123#1122123](https://askubuntu.com/questions/446682/how-to-install-ubuntu-on-portable-external-hard-drive/1122123#1122123)

---

### Post by oldfred on 2019-04-01
Only some systems will boot from an SD card.

If not you may be able to use a USB adapter, so SD card seen as USB device.

If you do not follow C.S.Cameron's advice, it gets a bit more complicated.
And it matters if you want UEFI or BIOS boot.
You have to partition in advance with correct partitioning, gpt for UEFI. You also can use gpt with BIOS boot but need a bios_grub partition. You also can then use the 35 year old MBR partitioning for BIOS boot.
And if BIOS you must install grub boot loader to MBR of SD card.
If UEFI, you will have to copy /EFI/ubuntu and /EFI/Boot from internal drive's ESP to /EFI/ubuntu and /EFI/Boot to ESP on SD card. 
The ESP is the efi system partition (FAT32) required for UEFI boot.

       UEFI/gpt partitioning in Advance:
[URL="http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu"]http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu

[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)
[/URL]

---

### Post by aadarshram2003 on 2019-04-02
Thank you for your advice guys! But, I followed this installation from an image file: [https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#in_Windows](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#in_Windows) 
It works on both of my laptops. At first, WIFI wouldn't work on my HP Pavillion, but after updating the kernel to the latest version and installing the required WIFI drivers, it worked like a charm.
I would appreciate if there is any way to update my version from 16.04 LTS to 18.04 LTS.

Cheers
Aadarsh..

---

### Post by oldfred on 2019-04-02
I always prefer new clean install.
It also becomes a way to test that your backup procedures are good if your new install is to a new partition or in your case a different flash drive.

Often new install is quicker for whatever reason.

[https://help.ubuntu.com/community/BionicUpgrades](https://help.ubuntu.com/community/BionicUpgrades)

---

### Post by Sam_Azgor on 2019-04-02
> **oldfred said:**
> Only some systems will boot from an SD card.

If not you may be able to use a USB adapter, so SD card seen as USB device.

If you do not follow C.S.Cameron's advice, it gets a bit more complicated.
And it matters if you want UEFI or BIOS boot.
You have to partition in advance with correct partitioning, gpt for UEFI. You also can use gpt with BIOS boot but need a bios_grub partition. You also can then use the 35 year old MBR partitioning for BIOS boot.
And if BIOS you must install grub boot loader to MBR of SD card.
If UEFI, you will have to copy /EFI/ubuntu and /EFI/Boot from internal drive's ESP to /EFI/ubuntu and /EFI/Boot to ESP on SD card. 
The ESP is the efi system partition (FAT32) required for UEFI boot.

UEFI/gpt partitioning in Advance:
[URL="http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu"]http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu

[/URL][https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)


Thanx for your suggestion.

---

### Post by aadarshram2003 on 2019-04-03
Thanks oldfred,
Will see how to do a quick clean install. Thanks for your help.

---

