---
title: "sony vaio s with insydeh20 bios install problem"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by The Squig on 2013-03-24
Update, new problem:

I disabled secure boot and for some reason wasnt hit with the read-only error when writing to /EFI/Boot/. Following these steps [http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/) I was able to load grub,
Thats the good news. The BAD news is that in order to get it to work i had to overwrite "EFI/Microsoft/Boot/bootmgfw.efi" with grubx64.efi. I made a backup of the original file but its just gone. I dont know if i failed to copy it or if it was overwritten somehow but its lost now anyways.

Without it windows wont boot. is there anyway to to fix this? or will i have to reinstall windows to get the original bootloader restored?



------------------------------
Hi, Ive been trying to set up ubuntu (12.10 64bit) dual boot with windows8 on my sony vaio laptop (SVS1312K3EW) without much luck. 

Ive followed these instructions: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  
I could not find any options in my bios interface to disable QuickBoot/FastBoot or Intel Smart Response (step 2) so i did not perform that step.

After rebooting, my laptop will not load grub but just boot straight into windows8. Ive run the boot-repair tool ([http://paste.ubuntu.com/5643853/](http://paste.ubuntu.com/5643853/)) but it wasnt able to fix it.

I tried to move the grub efi file to EFI/Boot but i was hit with an error like this one:

```
cp: cannot create regular file Read-only file system 
```
This bugreport describes it further: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477)

I have yet to try the workaround posted there though.

Ill continue to tinker with it but im hoping someone has already come up with a fix.

---

### Post by oldfred on 2013-03-24
Did you overwrite file before running Boot-Repair as it makes backup of everything.

You have both the efi partition sda3 and a recovery partition sda1 that show/EFI/Microsoft/Boot/bootmgfw.efi, did you overwrite both?

Also 
       copy of Windows efi boot files:
        
 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by The Squig on 2013-03-24
Thank you very much! mounted my windows partition and made a copy from the backup you listed. both windows and ubuntu boots fine now :D


> Did you overwrite file before running Boot-Repair as it makes backup of everything.
no but i ran the boot-repair from a usb live session so im not sure where it would have saved it.

> You have both the efi partition sda3 and a recovery partition sda1 that show/EFI/Microsoft/Boot/bootmgfw.efi, did you overwrite both?
no I did not touch the recovery partition, only sda3.

---

### Post by oldfred on 2013-03-24
Glad you got it working.

I would backup efi partition and all of Windows. And make a Windows repair flash drive.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

