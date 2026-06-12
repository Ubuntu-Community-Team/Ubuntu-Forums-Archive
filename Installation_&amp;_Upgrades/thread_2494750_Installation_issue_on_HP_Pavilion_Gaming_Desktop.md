---
title: "Installation issue on HP Pavilion Gaming Desktop"
date: 2024-01-25
forum: Installation &amp; Upgrades
---

### Post by raguelmoon on 2024-01-25
Dear all,
i have HP Pavilion Gaming Desktop 11th Generation running windows 11. Following is spec
i9, 32GB RAM, 8GB GPU, 2TB SSD(Lexar, NM620, M 2 PCIe, NVMe). I have created bootable ubs as per direction given on ubuntu installation tutorial and also given on other forums. Switched off EFI security but failed to install Ubuntu. I have also tried different usb. See the screenshot that shows when it got stuck every time. It hanged up, no mouse, keyboard work. Please help me.
thank you,

---

### Post by MAFoElffen on 2024-01-26
What version and release of Ubuntu Installer. What is the "8GB GPU"? Which model of i9 (i9-11900_)? Is fastboot turned off in BIOS? (it should be.) There are 8 HP Gaming desktop Models... Which model is it, so I can look up the specs?

Did you verify the sha256checksum of the downloaded image? Does the LiveUSB boot on another PC? The reason I ask these two question is that an RIP error with kernel panic usually indicates  that there is o return value for the next instruction to fetch from. If on an installed system, sometimees that is from moving in a mispatched file tha conuses the CPU with bad resulting instructions. 

*** But on an installer LiveUSB, that is usually from a bad image file. 

Check the image checksum. If not good, re-download it. If good reburn the image to the USB Flash drive.

---

### Post by raguelmoon on 2024-01-28
Thank you very much for reply. 8GB GPU means, a video card (nvidia RTX). The complete description is attached.

---

### Post by MAFoElffen on 2024-01-29
I think it has an NVIDIA® GeForce® GTX 1650 Ti... After verifying you have a good image, from the Grub2 menu, try the Safe Graphics Option.

---

### Post by raguelmoon on 2024-01-30
> **MAFoElffen said:**
> I think it has an NVIDIA® GeForce® GTX 1650 Ti... After verifying you have a good image, from the Grub2 menu, try the Safe Graphics Option.

I also tried with safe graphics option but failed to install. Should I tried with board's internal graphics card (output to monitor with it)?

---

### Post by raguelmoon on 2024-01-30
> **MAFoElffen said:**
> What version and release of Ubuntu Installer. What is the "8GB GPU"? Which model of i9 (i9-11900_)? Is fastboot turned off in BIOS? (it should be.) There are 8 HP Gaming desktop Models... Which model is it, so I can look up the specs?

Did you verify the sha256checksum of the downloaded image? Does the LiveUSB boot on another PC? The reason I ask these two question is that an RIP error with kernel panic usually indicates  that there is o return value for the next instruction to fetch from. If on an installed system, sometimees that is from moving in a mispatched file tha conuses the CPU with bad resulting instructions. 

*** But on an installer LiveUSB, that is usually from a bad image file. 

Check the image checksum. If not good, re-download it. If good reburn the image to the USB Flash drive.

How to verify? I checked that sha256checksum is ok.

---

### Post by raguelmoon on 2024-01-30
here is screen of error when I instal Ubuntu 18 version:

---

### Post by tea for one on 2024-01-30
> **raguelmoon said:**
> here is screen of error when I instal Ubuntu 18 version:
You have 11th generation Intel i9, why have you chosen a 5 year old version of Ubuntu?
Your screenshot shows "Windows is hibernated"

Boot into Windows
Download and create a bootable Ubuntu 22.04 or 23.10 disk
Power off Windows 11 without hibernation or encryption

---

### Post by ActionParsnip on 2024-01-30
error says "Windows is hibernated" you need to shut windows down then cold boot to the USB. Be sure to resize the NTFS in Windows to leave unpartitioned space for Ubuntu and, as with any large system change like this.....Backup your important data in case of catastrophe

---

### Post by raguelmoon on 2024-01-30
I have tried with 22 and 23 too but not successful

---

### Post by MAFoElffen on 2024-01-30
Go into Winodws Power Settings > Action of Power Button > "Turn Off"... This turns FastBoot mode off. 

The default is that when the power button is pushed it go to hibernate. This leaves to filesystem in an opened stated. (Not good)

---

