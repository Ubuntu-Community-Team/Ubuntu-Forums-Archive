---
title: "UEFI Live USB No boot option"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by falaki on 2013-08-25
I have a 32G usb flash drive with ubuntu installed via pendrive linux on a FAT32 partition at the start of my drive. But in my UEFI Bios there is no boot option for USB EFI. The partition table is GUID(GPT)

---

### Post by oldfred on 2013-08-25
Do you have secure boot option on?
If secure boot option is on, then only secure boot systems will boot. Ubuntu's standard installer will install in UEFI with secure boot, UEFI without secure boot or CSM/BIOS, but it totally depends on which mode you boot in.
Some systems will not let you boot anything other than Windows with secure boot on. 
Does your Windows boot with secure boot off as that sometimes is an issue also.

---

### Post by falaki on 2013-08-26
No I dont have secure boot( my windows installation has failed and i deleted the partitions. I'm on arch linux now). I have managed to install arch linux through uefi but ubuntu the uefi option doesnt come up. Would making a new partition table as the type mbr fix this?

---

### Post by falaki on 2013-08-26
Fixed used msdos file system instead of gpt

---

