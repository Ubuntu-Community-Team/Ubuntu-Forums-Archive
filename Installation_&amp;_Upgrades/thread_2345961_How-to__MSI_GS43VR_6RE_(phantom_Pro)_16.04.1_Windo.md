---
title: "How-to : MSI GS43VR 6RE (phantom Pro) 16.04.1 Windows10 dual boot"
date: 2016-12-09
forum: Installation &amp; Upgrades
---

### Post by electronico_nc on 2016-12-09
Hi all,

My notes about the installation (after a lot of failures trying Legacy boot mode and  UEFI with CSM) :

Laptop came with SSD M2 256G, HDD 1T, RAM 2*8G. ordered 2*16G RAM,  SSD M2 512G with a M2-to-USB3 adapter at same time.
Aim was to install Ubuntu on upgraded internal 512G, keep Windows10 on 256G SSD in M2-to-USB3 adapter and (of course) dual-boot the system.
(turned out that the original Toshiba SSD M2 didn't fit into the M2-to-USB3 adapter, so Ubuntu will be on the external SSD)


[LIST]
[*]installed factory Windows10
[*]Set Secure Boot to disabled in BIOS (access via SUPP key at boot), keep UEFI, fast boot disabled
[*]Boot from USB stick with Ubuntu 16.04.1 Desktop adm64 iso, choose install Ubuntu
[*]When it came to disk partitions, choose manual partitionning (last option)
[/LIST]
Internal SSD 256G (with Windows10) is /dev/nvme0n1
Internal HDD 1T is /dev/sda
External SSD 512G (with wanted Ubuntu) is /dev/sdb
On /dev/sdb : 
[LIST]
[*]Create an EFI partition 500M
[*]Create a /boot partition EXT4 1G
[*]Create a / partition EXT4 200G (prefer to keep place on this drive)
[/LIST]
Choose to install boot loader on /dev/sdb
Finish Ubuntu install as usual (selected third party software)
At reboot : access to BIOS and choose the  UEFI drives order, make ubuntu one first, windows second

Dual boot is OK, Windows10 and BIOS access are well displayed by grub.
External SSD has to be plugged-in to allow the laptop to boot (that doesn't distrub me)

Hope this will help some.

---

