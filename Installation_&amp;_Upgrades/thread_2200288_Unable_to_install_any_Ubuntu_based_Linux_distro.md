---
title: "Unable to install any Ubuntu based Linux distro"
date: 2014-01-18
forum: Installation &amp; Upgrades
---

### Post by vaidotas203 on 2014-01-18
Hello,

This is my first post, sorry if something is wrong.
I have used Linux for more than 5 years now on my laptop, which now has triple boot (Ubuntu/Manjaro_Net/Windows)

1 month ago I have build new computer with these parts:

Intel Core i7-4770K, Quad Core, 3.50GHz (Turbo: 3.90GHz), 8MB, LGA1150, 22nm, 84W, Intel HD 4600, Box
Gigabyte GA-Z87X-SLI, Z87, DualDDR3-1600, SATA3, HDMI, ATX
DDR3 Kingston HyperX 8GB (2x4GB) 1600MHz CL9 1.65V
HDD Seagate Barracuda 3.5'' 1TB SATA3 7200RPM 64MB x2
SSD Adata XPG SX900 128GB SATA3, Sparta 550/520MBs, IOPS 85K
Card Reader iBOX 85 in 1, USB, Black
DRW Samsung SH-224BB, SATA, Bare bulk, Black
THERMALTAKE V3 Black Edition Midi Tower black Window 120mm blue LED Fan ATX microATX 2x USB 2.0 HD Audio
PSU Fortron FSP700-50ARN (85+) 700W Active PFC
Gigabyte GeForce GTX 650 TI Boost, 2GB DDR5 (192 Bit), HDMI, DP, DVI, BOX x2

Using SLI but not RAID. Windows 8 works, however I am unable to boot ANY Ubuntu based distro, Arch based somehow loads but still with errors. Guessing there is some BIOS settings, which causes this, unfortunately BIOS has more settings, than cockpit of plain...
2 monitors, one connected via HDMI other via DVI to VGA adapter.

Tried to boot from USB and other CD, disk sum checked, no issues in there.
Some screens which I can see if I hit ESC during Ubuntu logo (sorry for flash):
[http://i.imgur.com/09adFKX.png](http://i.imgur.com/09adFKX.png)
[http://i.imgur.com/LJX9R4R.png](http://i.imgur.com/LJX9R4R.png)
[http://i.imgur.com/mNEqIoz.png](http://i.imgur.com/mNEqIoz.png)
[http://i.imgur.com/HCARum0.png](http://i.imgur.com/HCARum0.png)
[http://i.imgur.com/Y5PhRGK.png](http://i.imgur.com/Y5PhRGK.png)

Maybe somebody could suggest something?

---

### Post by oldfred on 2014-01-18
UEFI or BIOS installs of both Windows or Ubuntu. 
Whichever you choose they should be the same.
And with UEFI you have to have gpt partitioning on drives.

These were older Gigabyte boards, not sure if same issue carried to your model?
 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS mode) to set ACPI=Off.and nomodeset
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.


 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by vaidotas203 on 2014-01-18
It seems I am a bit blind as I can not locate nor ACPI nor IOMMU... Sorry, could you also guide under which tab it should or could be:
[http://imgur.com/a/xgKna](http://imgur.com/a/xgKna)

---

### Post by oldfred on 2014-01-18
I do not have an UEFI Gigabyte board. Yours may not have those settings since newer.

With nVidia you will also need nomodeset to get it to boot.
With UEFI you boot with grub and have to manually add nomodeset to linux line like first boot after install or until you install the nVidia proprietary driver from the repository.
At grub menu press e for edit, scroll to linux line and replace quiet splash with nomodeset.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

