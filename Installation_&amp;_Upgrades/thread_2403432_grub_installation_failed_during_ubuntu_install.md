---
title: "grub installation failed during ubuntu install"
date: 2018-10-11
forum: Installation &amp; Upgrades
---

### Post by robertvarga2 on 2018-10-11
Grub installation fails during Ubuntu 18.04 install. I have two hard drives: 1TB with Windows 7 and another one with 3TB (GPT) with a data partition and one for Ubuntu.
I have tried installing grub on both hard drives with the same result. I can currently boot into Windows.

Here is a link to the boot-info log:
[http://paste.ubuntu.com/p/WhhXgKk5Mk/](http://paste.ubuntu.com/p/WhhXgKk5Mk/)

I have already done a dual-boot setup on a laptop before with success, but this is configuration is different.
Any help is appreciated.

Thanks!

---

### Post by yancek on 2018-10-11
What happens, what error messages do you get when trying to install Grub?  At the end of the boot repair it tells you that because you have a GPT disk you need to create a BIOS boot partition in order to boot and install Grub.  THis can be done from GPArted which is on the Ubuntu install usb.  Not sure why you don't have windows code in the MBR of your windows drive but do have it on the larger drive where you install Ubuntu?

---

### Post by oldfred on 2018-10-11
Grub in UEFI mode will want to install to an ESP, usually gpt partitioned.
But you sda is Windows in BIOS boot and MBR.
Windows only boots in BIOS mode from MBR drives, so you cannot easily convert sda to UEFI boot.

So you need to install Ubuntu in BIOS boot mode. You can easily convert install to BIOS, but will need a 1 or 2 MB unformatted partition with bios_grub flag on HDD. And then in Boot-Repair's advanced options booted in BIOS mode install grub to sdb drive.


UEFI is for new systems and you seem to have newer hardware.
Older Windows 7 can be installed in UEFI mode, but its default is the now 35 year old BIOS/MBR configuration.

---

### Post by robertvarga2 on 2018-10-15
I created a 10 MB unformatted partition on sdb drive with the bios_grub flag. I have booted into installation in non-UEFI mode (I guess that is BIOS) and ran the installation with installing the GRUB on sdb. I get the same error message: [COLOR=#000000]'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.[/COLOR] What am I doing wrong?

---

### Post by oldfred on 2018-10-15
When you boot install media from UEFI boot menu you should have two boot choices.
But must have UEFI Secure boot off, or you may only have UEFI boot option.

One option should be clearly UEFI:flash drive and other is just flash drive which is BIOS boot option.

How you boot install media UEFI or BIOS is then how it installs. So if wanting to install the UEFI version of grub, you booted in UEFI boot mode.

---

### Post by robertvarga2 on 2018-10-16
I have managed to setup dual boot by creating a Ubuntu partition on the first disk - sda. This is not what I wanted, but it will have to make do. Thanks for the help, anyway!

---

