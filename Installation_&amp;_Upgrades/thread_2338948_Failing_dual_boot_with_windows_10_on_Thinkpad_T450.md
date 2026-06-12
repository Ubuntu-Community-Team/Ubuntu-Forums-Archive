---
title: "Failing dual boot with windows 10 on Thinkpad T450s"
date: 2016-10-03
forum: Installation &amp; Upgrades
---

### Post by thinksmad on 2016-10-03
Hi,


It has been a while since I am facing this issue. I have windows 10 on Lenovo Thinkpad T450s. I made a 16.04 LTS installation USB. At the end of the installation 
it asks to restart the computer and once its done it directly loads windows 10-- doesnt reboot into grub.
- Windows: UEFI
- Created separate 50GB partition before for Ubuntu
- Disabled Secure Boot and Fast Startup
- Installer made with Rufus [also tried Universal USB Installer from pendrivelinux]

If pointing to Ubuntu bootloader is and issue how do I do it. Can somebody help me out here please. Thanks

---

### Post by yancek on 2016-10-03
You haven't posted enough information for anyone to give  you realistic advice.  The best way to get that info is at the site  below where you can read about the boot repair software, download and  run it and post a link to the output here.  Make sure to select the  option to Create BootInfo Sumary and do not try to make any repairs.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have a pre-installed windows 10, it is most likely UEFI so reading the info at the site below would be useful to you.  One likely scenario is that windows is UEFI and your Ubuntu install is not.  The boot repair output will show this information.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by thinksmad on 2016-10-03
Hi,

plz find below the boot info

[http://paste2.org/8BB4f8zB](http://paste2.org/8BB4f8zB)

Thanks

---

### Post by oldfred on 2016-10-03
You have an UEFI system.
Windows is installed in UEFI boot mode.
But you show grub installed to MBR for BIOS boot and grub files in ESP - efi system partition for UEFI boot.
That grub is in gpt drive's protective MBR, will not matter, just never attempt to boot in BIOS/Legacy/CSM mode as it will not work as not even fully/correctly installed to MBR (no bios_grub partition).

Let Boot-Repair reinstall grub-efi-amd so we can be sure you have that version of grub installed.

What model Lenovo?

Some issues with various models of Lenovo. Often issues are common across models.
 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

