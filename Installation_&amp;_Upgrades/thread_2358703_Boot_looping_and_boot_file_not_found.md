---
title: "Boot looping and boot file not found"
date: 2017-04-16
forum: Installation &amp; Upgrades
---

### Post by fhmi on 2017-04-16
Hi, i just installed ubuntu. Then i remove my windows using os uninstaller. When i reboot my pc, it stuck at bios. When i tried to reinstall ubuntu using my pendrive, right before the grub appeared it says "error : file 'boot' not found. After the grub appeared i tried to install it back but it keep boot looping from black screen to ubuntu loading screen. I tried all listed on grub, "using ubuntu without installing, install ubuntu, oem install, check disc defect" when i check disc effect. One error found but i dont know what it is. I tried to rewrite the usb, the problem still remains the same. Please help me fix this :(

---

### Post by RobGoss on 2017-04-16
Hello and welcome, If this was a dual boot you cannot remove Windows after installing** Ubuntu** because you installed the Grub loader on the Windows **MBR** partition which is why you are not able to boot your machine

You could have just ran the live installer and tell the live installer to use the** entire disk **, everything should have been working if no issues

---

### Post by yancek on 2017-04-16
If you had just installed Ubuntu, why would you try to reinstall it after removing windows?  Don't see how that would help anything.  Which windows version did you have?  Did you install Ubuntu UEFI or MBR or do you know?

---

### Post by fhmi on 2017-04-16
I had install the ubuntu using the entire disk. Please do you hv any solutions to this :(

---

### Post by fhmi on 2017-04-16
I tried to reinstall ubuntu because after i uninstall my windows 10, when i reboot my pc it stuck at bios. I installed ubuntu uefi

---

### Post by oldfred on 2017-04-16
What brand/model system?
Some violate UEFI standard and use description to boot. And only valid description is "Windows Boot Manager".
But various work arounds depending on configuration.

Be sure to boot Ubuntu live installer in UEFI mode.
       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you run Boot-Repair, so not use auto fix, but advanced mode and include the "use the standard efi file" option.

---

### Post by fhmi on 2017-04-17
I use ASUS LAPTOP A555L. This what i get from boot summary [http://paste.ubuntu.com/24401345](http://paste.ubuntu.com/24401345). Please help me oldfred!! &#55357;&#56911;&#55356;&#57343;

---

### Post by oldfred on 2017-04-17
Your sda1 is shown as the ESP - efi system partion.
But also says it is NTFS, but the ESP must be FAT32?
Did you reformat it, which probably erased all the UEFI boot files?

If you can see data in sda1 back it all up.
Reformat sda1 to FAT32 and restore all data.
If no data and after reformat, you need Windows repair disk to restore Widnows boot files and can totally reinstall grub with advanced options in Boot-Repair to restore Ubuntu's .efi boot files into ESP.

You may be able to change format with Disks utility. But it is on same menu as format but you have to select not to erase data. Best to have backup if you can.

---

### Post by fhmi on 2017-04-18
Hi oldfred, thanks for helping me out. There is no data in sda1. I had insert windows repair disk and I dont really know what to chose. I tried to install the windows 10 but its says 'Windows cant find Microsoft Software License Terms. Make sure the installation sources are valid and restart the installation. Help me T.T. Will changing the harddisk solve the problems?

---

### Post by oldfred on 2017-04-18
Did you reformat sda1 to FAT32? You can use Ubuntu live installer for that.

Have not installed Windows.
But new UEFI systems have product key inside UEFI. So you have to boot in UEFI mode.
Some have said key is only valid for vendor version, but then I thought Microsoft released a version that works.
But you then may have lots of driver issues if not version of Windows from vendor.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

