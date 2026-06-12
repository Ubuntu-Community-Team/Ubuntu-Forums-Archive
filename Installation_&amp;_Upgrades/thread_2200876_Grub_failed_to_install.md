---
title: "Grub failed to install"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by kashif2 on 2014-01-21
I have got a new Dell Inspiron 5537 laptop. I have installed Windows 7 ultimate edition on it and am now installing [COLOR=#000000]Ubuntu 12.04.3 LTS to go along with Windows.

I am installing Ubuntu through a live USB. However, the installation is failing with following error:

[/COLOR]**grub-efi-amd64-signed failed to install into /target/**

I have then used the Boot-Repair live usb to rectify the grub error. This did not worked out as well. Boot-Repair log is at [http://paste.ubuntu.com/6793016/plain/](http://paste.ubuntu.com/6793016/plain/)

Any ideas how to get the grub issue to work and have Ubuntu work along Windows?

---

### Post by kashif2 on 2014-01-21
I am checking the thread [http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)

Following the instructions, I have updated grub. However, now I have to install grub in the bootloader (sdb1). Shall I perform apt-get install grub?

---

### Post by oldfred on 2014-01-21
New systems have UEFI and secure boot.
Windows 7 does not use secure boot, and default install is BIOS/MBR not UEFI/gpt. But you can convert a Windows 7 install to UEFI if desired.

It looks like you originally installed Ubuntu in UEFI with secure boot mode on. But you cannot use UEFI on a MBR(msdos) drive.

And Windows 7 does not convert gpt drives as used by all UEFI systems to MBR correctly as it does not delete backup gpt partition table. So grub does not install correctly. Use fixparts and re-install grub to MBR.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Since you have converted system to BIOS boot mode, be sure to always boot in BIOS mode, not UEFI.
      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by kashif2 on 2014-01-22
> **oldfred said:**
> New systems have UEFI and secure boot.
Windows 7 does not use secure boot, and default install is BIOS/MBR not UEFI/gpt. But you can convert a Windows 7 install to UEFI if desired.

It looks like you originally installed Ubuntu in UEFI with secure boot mode on. But you cannot use UEFI on a MBR(msdos) drive.

And Windows 7 does not convert gpt drives as used by all UEFI systems to MBR correctly as it does not delete backup gpt partition table. So grub does not install correctly. Use fixparts and re-install grub to MBR.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Since you have converted system to BIOS boot mode, be sure to always boot in BIOS mode, not UEFI.
      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I have followed the instructions give at the thread [http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows) to install grub and copy it to the bootloader.

I do have a dual boot option for both Ubuntu and Windows. However, there are several other entries as follows:

[COLOR=#333333][FONT=UbuntuRegular] [/FONT][/COLOR]

[LIST]
[*]"Ubuntu, with Linux 3.2.0-23-generic"
[*]"Ubuntu, with Linux 3.2.0-23-generic (recovery mode)"
[*]"Memory test (memtest86+)"
[*]"Memory test (memtest86+, serial console 115200)"
[*]"Windows Recovery Environment (loader) (on /dev/sdb1)"
[*]"Windows 7 (loader) (on /dev/sdb2)"
[*]"System Setup"
[/LIST]
Also, when Ubuntu loads, it runs the initialization commands in terminal mode and the desktop is visible only after the initialization process is finished.

---

