---
title: "Boot USB failure. See details."
date: 2020-09-26
forum: Installation &amp; Upgrades
---

### Post by arcanezoidpilot on 2020-09-26
Hello.
I'm trying to install (any) Linux distribution onto my desktop using a live-USB but 
I only receive error messages when starting to boot. I've never completed an installation.


The error message repeats
"AMD-Vi : Completion-Wait loop timed out" and "Kernal panic".


A 4GB live-USB formated in FAT32 is used.
Ubuntu 20.04 LTS placed on the drive using Rufus 3.11 and Etcher (seperate attempts)
Linux Mint, Debian, and PureOS were also attempted.


Actions already taken to resolve the issue:
Updated GPU, chipset, and BIOS drivers.
BIOS settings changed to "UEFI" and back to "Legacy".
When the option for a command line presented on boot menu, alternative kernal settings
were tried. They are as follows:
iommu=off
iommu=off AND amd_iommu=fullflush
amd_iommu=off
mem_encrypt=off
amdgpu.runpm=0
pci=noats


*PureOS did boot with the "iommu=off" but only once. The event could not be recreated.


Desktop Details:
Windows 10 64-bit
CPU: AMD Ryzen 5 2600
RAM: 16GB DDR4
MOBO: Gigabyte B450M DS3H
GPU: AMD Radeon RX 5700 XT (Gigabyte)
Storage:
PCIe 500GB
Samsung SSD 250GB
WD 1TB HDD


* I have no prior experience with Linux so I do not know many command prompts or lingo.
Thank you in advance for your guidance and patience.

In the attached pictures, you will see the “AMD-Vi” error that occurs when I don’t select install at the “Ubuntu install” page.
If I do select install (the first option), other errors occur as shown (in the smaller font).

---

### Post by QIII on 2020-09-26
Are you attempting to install a virtual machine?

---

### Post by arcanezoidpilot on 2020-09-26
Negative. I was not going to use a virtual machine.

---

