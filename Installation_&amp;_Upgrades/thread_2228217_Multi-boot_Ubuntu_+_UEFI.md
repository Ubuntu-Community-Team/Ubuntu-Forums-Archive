---
title: "Multi-boot Ubuntu + UEFI"
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by niek2 on 2014-06-06
Hi everyone,


I have installed Ubuntu on my laptop but while booting I still can't choose between Ubuntu - W7 and W8, only W7 and W8.


I have tried several fixes only they seem to be for non-EFI systems. Fortunately they didn't damage my windows boot sector. Unfortunately I can't boot into my Ubuntu installation.


My current configuration:
Disk 0:
SSD with 1 partition - NTFS: Windows 7 installation


Disk 1:
HDD with 4 partitions (actually more but I mention the most relevant ones):
Partition 0 - NTFS: Windows 8 installation + some programs
Partition 1 - NTFS: Personal data/documents
Partition 2 - EXT4: Latest version of Linux Ubuntu
Partition 3 - ?????: Recommended amount of SWAP memory


The EFI system is in Legacy mode so windows 7 can boot.


Does anyone know how to get Ubuntu to show up in my boot menu?

---

### Post by grahammechanical on 2014-06-06
I assume that the SSD has boot priority. When you installed Ubuntu where was Grub installed? Was it installed on to the SSD or the HHD? Try changing the boot priority to the HHD and see if Grub appears.

Regards.

---

### Post by oldfred on 2014-06-06
UEFI and BIOS are not compatible. 
Once you start booting in one mode, you cannot switch to another mode.
Or you can only boot from grub menu any system installed in the same mode as Ubuntu/grub.
Also Windows only boots in UEFI mode from gpt drives.
And Windows & Ubuntu only boot in BIOS mode from MBR drives.
Ubuntu will boot in BIOS/CSM or UEFI from gpt drives, but then cannot boot Windows 8 from grub.

So are all systems installed in UEFI boot mode?
Does each drive has its own efi partition. I think otherwise Windows will only have one entry in efi folder for grub to find and BCD inside Windows offers the choice of which Windows to boot.

---

### Post by niek2 on 2014-06-06
My system has the SSD as boot device priority. When I boot to the HDD it boots to Windows 8 without me having the option to choose.

Each drive has a EFI partition and are both GPT drives. I actualy don't really understand the UEFI system, I had to change some setting for my windows 7 installation, from EFI to legacy mode.

---

### Post by oldfred on 2014-06-06
May be best then to see all the details.

Post link to the Bootinfo Report:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

