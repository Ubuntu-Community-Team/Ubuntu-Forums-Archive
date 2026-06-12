---
title: "Cannot find Ubuntu 16.04 (Windows 7 and Ubuntu dual boot)"
date: 2016-06-09
forum: Installation &amp; Upgrades
---

### Post by sxiong0108 on 2016-06-09
Dear all,

I have a new Lenovo ThinkPad T460s with Windows 7 64-bit preinstalled, and I am trying to install Ubuntu 16.04 LTS 64-bit alongside with it. I followed the easy instruction for installation using a USB driver without any problem ([http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)). But when the laptop restarts, I can only find Windows 7 under Windows boot manager, the choice for Ubuntu doesn't show up. Windows7 runs normally. UEFI secure boot is off.


Now there are 4 primary partitions: C for Windows7_OS, Q for Lenovo_Recovery, and 2 unnamed volumes (<340 GB and ~7 GB). I plugged in the USB driver again and checked that Ubuntu was successfully installed on the 340 GB volume. Without the USB driver, I still cannot see Ubuntu.

What should I do? Thanks a lot in advance!

---

### Post by yancek on 2016-06-09
Probably the next step is for you to  boot the Ubuntu usb and go to the site below and download the boot repair software and run it.  Make sure you select the Create BootInfo summary option and do not try to make any changes.  You can then post a link to the output here and someone should be able to advise you.  You haven't posted enough details but the most likely thing is improper installation of the bootloader.  Also, which Installation Type option did you choose?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by X-RED_Tech on 2016-06-09
Windows 7 is almost always installed in legacy mode even in newer UEFI hardware. You probably installed Ubuntu in UEFI mode. You shouldn't be able to boot Ubuntu from Windows boot manager anyway. Both Windows and Ubuntu dhould be booting from Grub and have Grub chainload to the respective boot loaders.

As suggested in the post above install and run the Boot Repair but do not apply any correction. Instead generate a report and post it back here so we can see where you're at.

---

### Post by sxiong0108 on 2016-06-09
Here is the report:
[https://www.dropbox.com/s/nyubanc74y873pd/Boot-Info_2016-06-09__15h31.txt?dl=0](https://www.dropbox.com/s/nyubanc74y873pd/Boot-Info_2016-06-09__15h31.txt?dl=0)

Thanks for your advice!

---

### Post by oldfred on 2016-06-09
Your Windows 7 is installed in UEFI boot mode.
And Ubuntu is installed in BIOS boot mode.

While you can dual boot that way, you can only dual boot from UEFI boot menu or one time boot key like f10 or 12, not sure what Lenovo users.

Since Windows is UEFI better to have Ubuntu in UEFI boot mode.
If you boot live installer & Boot-Repair in UEFI mode it can convert install from BIOS to UEFI.

But some Lenovo's may need some work arounds:
 The thermal updates were submitted today for the Linux 4.6 kernel merge window and there's a very important fix for at least some newer Lenovo laptops.
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates)
Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side
Lenovo S20-30 BIOS install only
[http://ubuntuforums.org/showthread.php?t=2277003](http://ubuntuforums.org/showthread.php?t=2277003)
T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by grahammechanical on 2016-06-09
You have a motherboard with a UEFI boot system and a hard drive with GPT partitioning and according to Boot Repair you have Windows 8 installed in EFI mode. Look at the report for sda1. That partition is the efi_boot partition that is needed when installing an OS in EFI mode on a GPT partitioned drive. In that partition there are Microsoft EFI boot files. Which is correct. But there are no Ubuntu EFI boot files which is not correct if Ubuntu was installed in EFI mode.

Look at sda5. That is a bios_boot partition. That bios_boot partition is needed if we install Ubuntu in BIOS/Legacy/CSM mode on a GPT partitioned drive. And that is where Ubuntu has put its boot files.

This is the point. If Windows is installed in EFI mode then we run the Ubuntu live session in EFI and that will install Ubuntu in EFI. Otherwise we get the situation you are in.

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if Ubuntu is the only operating system on your computer, then it does not matter whether you install Ubuntu in UEFI 
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Boot Repair says

> The boot of your PC is in Legacy mode. Please change it to EFI mode. Please use Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")) which contains an EFI-compatible version of this software. ((use it from live-USB, not from DVD)) 

> Warning: continuing without internet would leave your system unbootable. Please connect internet.The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.Do you want to continue? 
> The default repair of the Boot-Repair utility would purge (in order to fix packages sign-grub) and reinstall the grub-efi-amd64-signed of sda6, using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s    backup-and-rename-efi-files 

> please do not forget to make your BIOS boot on sda1/efi/.../grub*.efi file! If your computer reboots directly into Windows, try to change the boot order in your BIOS.

If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.For example you can boot into Windows, then type the following command in an admin command prompt:bcdedit /set {bootmgr} path \EFI\...\grub*.efi

As far as I can see, your options are to accept the Boot Repair recommended repair or re-install Ubuntu in EFI mode. Is this a 64bit version of Ubuntu (amd64)? I do not think that the 32 bit version (i386) will install in EFI mode,

Regards.

---

