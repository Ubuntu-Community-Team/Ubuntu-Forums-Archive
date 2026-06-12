---
title: "Samsung NP355V4C laptop - won't boot ubuntu after installation, Grub not installed?"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by man_bash on 2014-01-08
Hello everyone

I'm trying to install Ubuntu (12.04) on my laptop, a Samsung NP355V4C-S01CA. The laptop specs are as follows:
CPU - AMD A10-4600M
GPU - AMD Radeon 7660D + Radeon 7670M
RAM - 8 GB DDR3-1600, CL9
HDD - 750 GB.

I had partitioned the HDD prior to installation, with 160 GB Windows partition, 125 GB Ubuntu partition, a ~400 GB data partition, and a ~22 GB recovery partition. I have done a number of Ubuntu installs on my desktop, as well as on my old netbook.

I did an install from a USB key, tried running from the USB stick, everything seemed fine: the GPU was recognized OK, the LAN and WiFi even, installer saw Windows partition and asked me if I wanted to import settings from it, and so I proceeded with installation, checking off boxes to install updates and the 3-rd party software. The installation had gone on (seemingly) without a hitch, but after the installation the laptop had proceeded to boot straight into Windows. Usually, on my desktop, Grub installs, and I see the options of what to boot (usually Ubuntu, recovery mode, and Windows(es)). So I went ahead, and, using BCDEdit, tried adding the Ubuntu partition to list of OSs, which had also failed. I am currently at my wits' end on what to do. I have seen many reports online that people were able to get linux running on this laptop (mostly from Russian users), and [linlap reports]("http://www.linlap.com/samsung_np355v4chttp://") the compatibility as "Good" with 3 ratings as "Excellent" and 5 as "Good", with no other ratings. Here on [UbuntuForums Hardware Incompatibility List]("http://ubuntuforums.org/showthread.php?t=361237&page=66"), a user reports that the biggest issues are not actuating the secondary GPU in Dual Graphics mode and the Fn-keys not working. I could run it in a VM, but I want to avoid doing so.

Any help is much appreciated.

---

### Post by ubfan1 on 2014-01-08
Try the efi menu to list the devices/OSes to boot (usually a function key early in the boot sequence) to see if you have ubuntu listed, and try to boot it (grub should display).  If that works, try booting Windows from grub. If that works, you can move the default boot to be the ubuntu entry, using efibootmgr.  Some machines just don't boot   Windows from grub, even with all the corrected grub commands, so in that case, you might just use the efi-menu to boot what you want (or make the default your most commonly used OS).

---

### Post by man_bash on 2014-01-08
Re: ubfan1
Since this is a laptop with little support, I tried pressing all keys but the F2 (which is for BIOS). One of them worked (I think). A menu showed up options to boot from the HDD or the DVDROM, but no GRUB. Selecting HDD loaded Windows 7 only.

---

### Post by ubfan1 on 2014-01-08
Just be sure, you machine is not a UEFI machine is it?  The linlap (link broken with extra http) referred to "UEFI settings" and I am a little confused.  If you do not have a UEFI machine, I'd suggest just running the live media and running sudo grub-install /dev/sda   on it.

---

