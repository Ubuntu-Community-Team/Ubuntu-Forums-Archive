---
title: "ubuntu install successful; after restart, bootdevice not found"
date: 2017-08-16
forum: Installation &amp; Upgrades
---

### Post by anniej267 on 2017-08-16
Hello,

I installed ubuntu onto a new HDD with a usb stick (because this laptop doesnt have a disk drive), and after it finished installing, it tells me to restart, and then brings me back to the same grub menu of testing ubuntu or installing it or checking the disk for defects.  I turned the computer off, and took out the usb stick, and powered it back on, only to be met with the message that "bootdevice not found" and "please install an operating system on your hard disk".  I start it up again with the usb stick inserted and "test" ubuntu and the HDD has a bunch of files and folders on it, which I assume is the ubuntu installation.  I ran boot-repair and it said it was successful, but it didnt change anything.  I messed around in the bios to change the boot order and it didnt really do much.  Ive been searching online for the past few hours trying to figure out what to do, but nothing has worked.  I would appreciate any help. 

(the computer is an hp 645 g1 laptop with a brand new western digital HDD 500g capacity)

---

### Post by shridhar-kapshikar on 2017-08-17
Try to disable a secure boot and start it again. Let me know the results.

---

### Post by anniej267 on 2017-08-17
I looked in the bios and secureboot was already disabled. There were a couple other settings that mentioned secureboot (under set security level there was a secureboot item that came with three options: Change View and hide, and then there was a check box under secureboot called "clear secureboot keys").

---

### Post by oldfred on 2017-08-17
Do not clear keys.

HPs usually need a work around, and if you ran Boot-Repair it may have already done one work around which is copy shimx64.efi to the fallback or hard drive boot entry of /EFI/Boot/bootx64.efi. That usually with HP is already just a copy of the Windows boot file.
Can you boot a hard drive entry from UEFI one time boot key. Or does the ubuntu entry then work?
       HP - escape + F9 for boot menu, F10 for bios setup 

Older threads where users manually copied shim, before Boot-Repair did it.
If Boot-Repair did not do copy, use advanced mode and check the 'use the standard EFI file' option


 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

See link below in my signature.

 Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

