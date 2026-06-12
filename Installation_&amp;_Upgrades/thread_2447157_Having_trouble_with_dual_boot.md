---
title: "Having trouble with dual boot"
date: 2020-07-13
forum: Installation &amp; Upgrades
---

### Post by hranto on 2020-07-13
[COLOR=#1A1A1B][FONT=&quot]Hey guys, so I am bit stuck trying to dual boot ubuntu on an Aurora r10. I followed some tutorials, shrunk my partitions, and created the bootable usb, pressed f12 on start up and selected to install ubuntu, and I am seeing a crazy screen that looks like everything is broken. I have tried with 18.04 and 20.04 and both have given me the same result. Has anyone seen anything like this before? Any help would be super appreciated[/FONT][/COLOR]

---

### Post by oldfred on 2020-07-13
Your system has nVidia?
If so you need nomodeset boot parameter to boot. 
New versions of Ubuntu now offer to install proprietary nVidia driver as part of install, or you need nomodeset on boot of install until you add the nVidia driver from the Ubuntu repository.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

For general UEFI install info see link in my signature below.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 

Have you updated UEFI and SSD firmware?

Many of Dell issues are common with Alienware.
[https://www.dell.com/community/Linux-General/Area-51m-help-installing-Linux-as-Dual-Boot/td-p/7318506](https://www.dell.com/community/Linux-General/Area-51m-help-installing-Linux-as-Dual-Boot/td-p/7318506)
Alienware Area 51 R4 16.04 UEFI update
[https://ubuntuforums.org/showthread.php?t=2397456](https://ubuntuforums.org/showthread.php?t=2397456)
[https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4](https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4)

---

### Post by hranto on 2020-07-14
So I tried the suggested nomodset change and it definitely got further. I see a bunch of commands running and everything looks okay for about a minute and then I get the weird screen again. 

Do I need to change the SATA operation from RAID to AHCI? I don't even have a SATA drive.

For the firmware updates. Is this necessary? This is a brand new machine

I keep seeing instructions to go into bios and disable fastboot and secure boot, but I don't see this anywhere in my ui. All i see in the boot tab is Boot List Option which is set to UEFI, an option to enable usb boot support and then boot options priorities.

Sidebar: I can't seem to figure out how to post images in this thing orz

Thanks for all the help

---

### Post by CelticWarrior on 2020-07-14
You may want to check for CSM and make sure that's disabled. This guarantees you're booting the installation media in UEFI mode and then installing in this proper mode.
Also better to disable Secure Boot with a Nvidia card that requires proprietary drivers as mentioned above. If there isn't an explicit settings try finding "OS selection" or similar where "Windows ...." means Secure Boot enabled and "Other" means disabled. Other variants may exist.

---

### Post by oldfred on 2020-07-14
With Dell it is f2 for UEFI settings & f12 for boot options.
You still need to check UEFI version versus current available update, often new systems still get a new update. Some SSD update from system vendor and some have their own. My Samsung has its own update ISO and when booted looked like an old DOS or simple screen that only offered to update firmware for my model.
You need to change from RAID or probably Intel RST to AHCI. If dual booting with Windows you need to install Windows AHCI driver first, or Windows will not boot.  Or you temporarily change back to RST and Ubuntu will not then boot.

Microsoft has required vendors to allow change from UEFI secure boot. Do not think that has changed, but may have been because Windows 7 did not support Secure Boot.
Many systems seem to call the mode "Windows" or "Other". But fine print used to say use "Other" for Windows 7 since it did not support UEFI Secure Boot.

Some systems require you to set an UEFI password to open up more settings. But never lose that password or reset to blank when done or you may convert system to a brick.

Best to download manual if have not done that and review the settings. Often lot more explanation.

[https://www.dell.com/community/Linux-General/Area-51m-help-installing-Linux-as-Dual-Boot/td-p/7318506](https://www.dell.com/community/Linux-General/Area-51m-help-installing-Linux-as-Dual-Boot/td-p/7318506)

You can attach screen shots with the Forum's advanced editor & the paperclip icon. Do not post in line.
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

---

