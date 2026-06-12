---
title: "Can't Boot Windows 10 After Installing Ubuntu 18"
date: 2019-12-25
forum: Installation &amp; Upgrades
---

### Post by elixirtrip on 2019-12-25
Hi,


I have a dual-boot setup with Windows 10 and Ubuntu 18.04. Each OS is installed on a separate partition of one hard drive. Unfortunately, after completing the Ubuntu install and rebooting, I see no sign of the Grub menu. I followed several sets of instructions for reinstalling Grub, with no luck!


No matter what I try, I can't seem to make Grub appear, and now I can't get back to Windows 10.

I tried Boot-Repair and many other google advises...

[ATTACH]284680[/ATTACH]

---

### Post by CelticWarrior on 2019-12-25
There are NO SIGNS of Windows in your report. If you selected the "erase and install..." option during the installation, I'm afraid the installer did just that as per your instructions. Meaning, if not clear by now, that you overwrote Windows.

---

### Post by oldfred on 2019-12-25
Your ESP - efi system partition is p7 on your NVMe drive.
But that is not normal with Windows, so it may be that you installed Windows in the old BIOS/MBR mode. And if you forced conversion to gpt partitioning that would break Windows. But Ubuntu will install to a MBR drive in UEFI boot mode (it really should not).

And you cannot have Windows in the old BIOS/MBR configuration and Ubuntu in UEFI configuration on the same drive.
Windows boots from a primary NTFS partition with the boot flag.
UEFI boots from an ESP which has the boot flag. 
And only one boot flag per drive.

Microsoft has required vendors to install Windows in UEFI boot mode since Windows 8 released in 2012. Did you install yourself and boot install media in old BIOS boot mode.?

To boot Windows you need to move boot flag back to first NTFS partition (assuming it is the one with boot files). Report did not show any details.
And reinstall/install a Windows or Windows type boot loader to MBR.
You may be able to use Boot-Repair's advanced mode and install syslinux boot loader which works like Windows boot loader. But better to use your Windows repair/recovery or install flash drive's repair console to fixMBR.

Or you can backup your data and reinstall Windows in UEFI boot mode & reinstall Ubuntu in UEFI boot mode.
Both Windows & Ubuntu install in the boot mode you use to boot install media.

       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-]("https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations")

---

### Post by elixirtrip on 2019-12-26
Thank you very much for replay and help! I will try it. But for now more detailed report: [http://paste.ubuntu.com/p/nRMMyYnKfK/](http://paste.ubuntu.com/p/nRMMyYnKfK/)

---

### Post by oldfred on 2019-12-26
It shows drive as dos, which is MBR partitioning.

One disadvantage of Windows 8 or 10 in BIOS boot mode and dual booting is that Windows keeps turning on fast start up. Or occasionally it needs chkdsk. Grub only boots working Windows, so then you have to temporarily restore a Windows boot loader, fix Windows, and then restore grub.

With UEFI, both Windows & Ubuntu share an ESP and both have boot files. You normally can boot Windows from grub, but when Windows breaks, you can directly boot Windows from UEFI boot menu and often then turn off fast start up or use internal repair console (f8). Still best to have both Ubuntu live installer & Windows repair/recovery flash drives.

---

