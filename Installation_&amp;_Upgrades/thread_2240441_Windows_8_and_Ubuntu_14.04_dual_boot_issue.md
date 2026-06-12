---
title: "Windows 8 and Ubuntu 14.04 dual boot issue"
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by OscarGot on 2014-08-20
I've installed ubuntu 14.04 after install windows 8 and am having trouble booting into Windows 8. When I attempt to boot up windows 8 I am always stuck in some recovery interface after Windows tries to automatically fix the boot loader. I've looked around the forums for similar issues and have used boot-repair but it doesn't seem to help. Also I'm able to boot into ubuntu if I turn off secure boot. 

Here is a pastebin from after running boot-repair: [http://paste.ubuntu.com/7996822/](http://paste.ubuntu.com/7996822/)

Any help would be appreciated thank you!

---

### Post by oldfred on 2014-08-20
You have Windows installed in UEFI boot mode, and you installed Ubuntu in BIOS/CSM/Legacy boot mode.

The two modes are not compatible, so you cannot boot Windows from grub menu. Once you start booting in one mode you cannot switch. You should be able to boot either system from UEFI boot menu, but may have to turn on/off UEFI or CSM/BIOS settings. Many newer systems auto switch and then you can use the one time boot key, often f12 or f11 depending on system to choose which system to boot with.

BIOS boot mode does not have a secure boot. UEFI can be either secure boot or not. Currently there is a bug in grub and with secure boot on it cannot boot Windows 8.1 from grub menu. 

Boot-Repair can convert a BIOS install to UEFI install in advanced options. It uninstalls grub-pc and installs grub-efi. Not sure if it works with trusty as grub-efi has changed to grub-efi-amd64 and it needs to run that, but I believe others have had it work. Make sure Internet is working as once grub-pc is uninstalled and before new grub-efi-amd is installed you could not reboot.

How you boot installer is how it installs. If Windows is UEFI, best to boot Ubuntu install flash drive in UEFI mode and install in UEFI mode.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

Do not reinstall Ubuntu except with Something Else manual install option. Major bug erases entire hard drive with any of the auto install options on a reinstall.
       Reinstall says overwrite Ubuntu but it also erases existing Windows.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

