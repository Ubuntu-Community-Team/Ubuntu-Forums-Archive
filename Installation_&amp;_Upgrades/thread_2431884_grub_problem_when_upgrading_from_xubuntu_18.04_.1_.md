---
title: "grub problem when upgrading from xubuntu 18.04 .1 to ubuntu 19.10"
date: 2019-11-23
forum: Installation &amp; Upgrades
---

### Post by brubix on 2019-11-23
Hi All,

I have 2 disks on my pc (one for OS, one only for datas).
Disk one contained windows 8.1 and xubuntu 18.04. It booted with grub 2.2. After testing ubuntu 19.10 :KSon a VM, i decided to install it on the xubuntu 18.04 partition
with a iso written on usb key. I chose "Replace Ubuntu" and install began correctly (except i couldn't uncheck upgrade while install) but 
at the end, when grub should be installed, a popup windows told me grub failed and install program crashed :(. Then a small bug report was automaticaly intended
to be sent to the team. unfortunately, i didn't have network at this stage. I restarted the computer, noticed grub changed from version 2.2 to 2.4 and stalled on command line.
I tried a new install from live session and got the same problem. I ran boot-repair from a new live session but i don't understand the problem (efi pb  ??). Ubuntu 19.10 files 
seems to be actually present. My kubuntu partition was split in 2 with a new efi fat32 partition.
 To recover my windows system, i overwrote the "boot chain system".
I'm curious to know what was going wrong and what i can do to reinstall dual-boot which perfectly worked before.
boot-repair report is in attachment.
Thank for your advice.

Bruno

---

### Post by oldfred on 2019-11-23
You cannot have mixed UEFI & BIOS boot with Ubuntu & Windows on same drive.
Windows in BIOS mode requires MBR(msdos) partitioning and boot flag on primary NTFS partition with Windows boot files.
UEFI requires boot flag on ESP - efi system partition which is FAT32. Windows reequires gpt, UEFI recommends gpt, but Ubuntu lets you install in UEFI mode to MBR (perhaps it should not). 

You can only have one boot flag per drive.
Move boot flag back to sda1 with gparted. Reinstall Windows boot loader and make sure it works. And make sure Windows fast start up is off.
Then you can restore grub to MBR.

One disadvantage of Windows 10 and BIOS/MBR is grub only boots working Windows. Or Windows that does not need chkdsk or has fast start up on. Windows with updates will turn fast start up back on, then grub will not boot it. Or Windows gets corruption and needs chdsk and grub will not boot it. You then have to go thru dance of restoring Windows boot loader, boot Windows and see if you can repair from Windows or Windows repair console, and then restore grub to dual boot.

UEFI lets you directly boot Windows from UEFI boot menu. So with newer UEFI hardware better to have all installs in UEFI boot mode.

In your case with two BIOS/MBR drives, you may want to keep  Windows boot loader in sda, but install grub to sdb and set UEFI/BIOS to boot sdb as default. Then when grub does not boot Windows, you can change BIOS to boot sda.
But I would still keep both Windows repair/recovery flash drive and Ubuntu live installer available to make repairs.

---

### Post by brubix on 2019-11-23
Thanks a lot for your answer :D.

If i understand, i installed a uefi distro which was not my intention (certainly because it started as uefi boot usb key) . so your suggestion to make an new install with a
grub written on sdb seems good to me. I think i should go in the "installation type" dialog and select sdb in "device for boot loader installation" . Am i right ?
 But now i recovered windows and partitions were all set, i don't want the grub install creates another one fat32 partition on my sdb to store its uefi loader.
Is it possible in this "semi-automatic" way ? or should i use some tools in a live session ?
By the way, it's strange that ubuntu 19.10 decided to erase my grub that worked perfectly instead of update it.

Bruno

---

### Post by oldfred on 2019-11-23
The selection of UEFI or BIOS for both Windows & Ubuntu is only based on how you boot install media.
So if you want BIOS/CSM/Legacy boot be sure to boot flash drive in that boot mode.
My system shows UEFI boot & BIOS boot separately. Most just have a "UEFI:flash" and "flash" setting where flash may be name of flash drive or pmap, and one without UEFI: is the BIOS boot.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

This shows screens, so you know which way you actually booted.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by brubix on 2019-11-24
Thank you for the links. As i got windows back and still have my linux partitions, i will do a new try
after checking my bios settings better.

Bruno

---

