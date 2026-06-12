---
title: "Dual boot Ubuntu Studio and Windows 8.1"
date: 2015-01-07
forum: Installation &amp; Upgrades
---

### Post by jrdobelmann on 2015-01-07
I recently got a new HP laptop preinstalled with Windows 8.1.  I was able to disable Secure Boot and turned on Legacy Mode, since the Live USB I have doesn't have UEFI.  I was able to install Ubuntu Studio, but now, whenever I want to boot into Ubuntu Studio, I have to boot into Windows, access the Boot Options Menu, select boot from USB (UEFI), let the computer fail to boot, and then it takes me to the OS Boot Manager.  Is there a simpler way I can get to the OS Boot Manager without having to do all of this?

---

### Post by oldfred on 2015-01-07
UEFI & BIOS are not compatible, so you have to reboot to change modes.
Can you directly boot from one time boot key, perhaps f10?

You can use Boot-Repair's advanced mode to convert BIOS boot to UEFI boot. It runs the commands to un-install grub-pc(BIOS) and installs grub-efi-amd64(UEFI)

HP's are not dual boot friendly in UEFI mode. They modify UEFI to only let you boot by the Windows description. But the hard drive entry still works, so many HP users change the hard drive efi partition entry /EFI/Boot/bootx64.efi to really be grub or shim & directly boot grub.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)


Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

---

### Post by jrdobelmann on 2015-01-08
I was able to get Ubuntu Studio to work with UEFI.  Thanks for the help!

---

