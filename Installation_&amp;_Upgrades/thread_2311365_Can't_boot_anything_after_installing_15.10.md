---
title: "Can't boot anything after installing 15.10"
date: 2016-01-26
forum: Installation &amp; Upgrades
---

### Post by johnlocke2342 on 2016-01-26
Hi everyone.
I started a computer repair formation in Paris. I bought parts for the new PC I wanted to buy for months (Core i7 4790K, Gigabyte Z97X Gaming 5) to train on it. I've been trying to install Ubuntu for weeks now as the liveUSB kept asking for a username and password at boot. I realized today it might be a bug whilst resigning in installing in English then installing support for my language (French). So I had a 480 GB SSD GUID formatted with 320 GB for Windows (and OS X should I decide to turn it into a hackintosh someday) and 120 GB for Ubuntu. Tonight I managed to complete the install for Ubuntu, choosing to install GRUB on the partition I was installing Ubuntu on (which always worked flawlessly on other PCs I owned). Upon reboot, I had the surprise to not being able to boot Ubuntu... nor Windows 10, which was working flawlessly (except by the fact it's Windows of course). I rebooted into my Live USB, trying to reinstall Ubuntu, installing GRUB on the default place. Everytime I tried the install crashed at some point, no matter what mode I chose to install from.

How can I get Windows 10 and Ubuntu to boot without wiping everything ?

Thanks in advance.

---

### Post by oldfred on 2016-01-26
If drive is gpt(GUID) and Windows 10 is installed then you are using UEFI.
You need to install Ubuntu in UEFI boot mode. And how you boot install media UEFI or BIOS is then how it installs.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens ( 10 should be almost identical)
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Gigabyte motherboards have a few issues particularly IOMMU.
      
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

---

### Post by johnlocke2342 on 2016-01-27
Hi and thanks for the answer.
I managed to install Ubuntu in UEFI mode (why, Why, WHY????? didn't I think about it). After the install, upon reboot I saw the purple background GRUB is usually on, but no GRUB. It booted right into Ubuntu.
Wanting to test if Windows would boot I selected "Shut down", then reboot. Now my PC is stuck on the mobo's big logo. It boots no further.

Thanks in advance.

---

### Post by oldfred on 2016-01-27
Not sure if your Motherboard has fast boot settings which are different than Windows fast start up, but you need to turn those off or try rebooting cold boot or power off. And hold power switch for 10 sec or so to make sure all residual power is drained. Then boot into UEFI or one time boot key by pressing correct key immediately.
Fast Boot in UEFI assumes everything is identical every time you boot, which often is the case and it speeds booting. But if any changes you need normal boot that checks hardware, UEFI settings & gives you enough time to get into UEFI to change settings if needed.

My Asus motherboard had settings for both cold boot & warm boot and delay on fast boot.

---

