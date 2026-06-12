---
title: "internal hard drive is not mounted after installing ubuntu 18.04"
date: 2018-05-17
forum: Installation &amp; Upgrades
---

### Post by arnold-dp94-x on 2018-05-17
[COLOR=#333333][FONT=Ubuntu]i want to install ubuntu 18.04 on my acer es1-132-c7kk. My first OS is win10. I use rufus 2.18 to create live USB with partition scheme and target system type GPT UEFI. When installing, i choose "something else" cause i want to delete my win10 partition and create new partition for ubuntu.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]/dev/sda1 efi
/dev/sda2 ext4 /
/dev/sda3 ext4 /home
/dev/sda4 swap[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]There is no problem when installing process. But after installed and rebooted, "No Bootable Device" shown up. I've check with live usb, my internal hard drive isn't mounted and mount button on gparted is greyed out. I already set auto mount and reboot but still "No Bootable Device".[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]What should i do to install this ubuntu on my laptop correctly ? does my laptop only support windows ? i don't know if my pc support uefi or just legacy coz no option "UEFI only", "legacy only", and "both"...just disabled or enable secure boot...

*i've tried to use partition scheme and target system type MBR scheme BIOS or UEFI and error GRUB installation failed showed up.. the message is "the 'grub-efi-amd64-signed' package failed to install into / target/. Without the GRUB boot loader, the installed system will not boot."[/FONT][/COLOR]

---

### Post by ajgreeny on 2018-05-17
Did you format sda1 as fat32 which is necessary for the EFI partition?

Let's see the output from a live system of ```
sudo parted -l
``` which will tell us a lot more.
You might also run **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by yancek on 2018-05-17
An Acer requires you to set "trust" in the BIOS to install another operating system, have you done that?  If you don't have a user manual, you can search here at the Ubuntu forums as there are numerous posts in regard to this problem.  When you boot, do you have a key to select boot options?  Do you have an option to boot from EFI file?  Do you see an Ubuntu entry?

---

### Post by arnold-dp94-x on 2018-05-17
*update sry, i've just realise my /dev/sda1 efi type is ext4...i just choose from create partition - use as : EFI system partition. I dont know how to change it to fat32. Do additional mount point "/boot" is required ?

everytime i try to reinstall with gpt partition UEFI and create new partition always failed. 

"GRUB installation failed"

"The 'grup-efi-amd64-signed' package failed to install into /target/. Without GRUB boot loader, the installation system will not boot"

package
ebiquity 18.04.14

problem type
bug

apportVersion
2.20.9.0ubuntu7

---

### Post by arnold-dp94-x on 2018-05-18
> **yancek said:**
> An Acer requires you to set "trust" in the BIOS to install another operating system, have you done that?  If you don't have a user manual, you can search here at the Ubuntu forums as there are numerous posts in regard to this problem.  When you boot, do you have a key to select boot options?  Do you have an option to boot from EFI file?  Do you see an Ubuntu entry?


[COLOR=#000000]set trust in the bios ? that's new to me. i already enabled key to select boot opt which is f12, the only boot option i got is USB Flash Drive : Adata USB Flash Drive without UEFI word. yes i saw ubuntu entry and it directed me to black screen with 4 opt, try ubuntu, install ubuntu, check disk and 1 other opt i forgot. 

update : that trust setting, i already set supervisor password on bios n "Select an UEFI file as trusted for executing" did not show up.[/COLOR]

---

### Post by arnold-dp94-x on 2018-05-18
> **ajgreeny said:**
> Did you format sda1 as fat32 which is necessary for the EFI partition?

Let's see the output from a live system of ```
sudo parted -l
``` which will tell us a lot more.
You might also run **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.     
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.


[http://paste.ubuntu.com/p/6XjSJgVRK3/](http://paste.ubuntu.com/p/6XjSJgVRK3/)  here's the link from boot-repair

---

### Post by oldfred on 2018-05-18
Most systems also need an update to the UEFI.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by arnold-dp94-x on 2018-05-19
> **oldfred said:**
> Most systems also need an update to the UEFI.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)


well, my currently bios version v1.15, the new one v1.19 do i need to update my bios ?  emm im gonna install windows first to get my bios updated.
[IMG]http://i64.tinypic.com/1tmupz.jpg[/IMG]

---

### Post by oldfred on 2018-05-19
Please attach screen shots not post in line.
Easy to add screen shots with Forum's advanced editor and paperclip icon.

You do need to update UEFI/BIOS.
Some systems do not need Windows to update. UEFI can directly read from FAT32 formatted partition the update file. Not sure about Acer.
My motherboard has 3 ways to update, Windows, directly from UEFI, and a DOS flash drive.

UEFI also need updates for Meltdown and Spectre CPU vulnerabilities. Vendors have to update UEFI and Windows & Linux have updated systems.

---

### Post by arnold-dp94-x on 2018-05-19
> **oldfred said:**
> Please attach screen shots not post in line.
Easy to add screen shots with Forum's advanced editor and paperclip icon.

You do need to update UEFI/BIOS.
Some systems do not need Windows to update. UEFI can directly read from FAT32 formatted partition the update file. Not sure about Acer.
My motherboard has 3 ways to update, Windows, directly from UEFI, and a DOS flash drive.

UEFI also need updates for Meltdown and Spectre CPU vulnerabilities. Vendors have to update UEFI and Windows & Linux have updated systems.


sry for that screenshot. I've already upgrade BIOS to v1.19 and still no "trust UEFI file" option idk what's wrong with this acer. No Legacy option, no trus uefi file option. i've installed ubuntu 18.04 but efi already fat 32, still "no bootable device". Do i need to set password for User and HHD0 in BIOS too ? or erase all secure boot setting ?

[http://paste.ubuntu.com/p/6XjSJgVRK3/](http://paste.ubuntu.com/p/6XjSJgVRK3/)[COLOR=#000000]  << i dont understand what in this link said, no boot loader is installed in the MBR of /dev/sda, why MBR ? i installed with GPT partition scheme[/COLOR]

---

### Post by oldfred on 2018-05-20
Gpt has a protective MBR. That is/was so older partitioning tools that only worked with MBR, would see one large gpt partition on drive or know drive was used. That MBR could also be used to install a BIOS boot loader on gpt drives.

UEFI only boots from the ESP - efi system partition.

Did you go thru several of the links (post 7) on users that have Acer and what they did, some explain better than others.

---

### Post by arnold-dp94-x on 2018-05-20
> **oldfred said:**
> Gpt has a protective MBR. That is/was so older partitioning tools that only worked with MBR, would see one large gpt partition on drive or know drive was used. That MBR could also be used to install a BIOS boot loader on gpt drives.

UEFI only boots from the ESP - efi system partition.

Did you go thru several of the links (post 7) on users that have Acer and what they did, some explain better than others. 

yep i did, well lucky them, they got [COLOR=#000000]"Select an UEFI file as trusted for executing:" [/COLOR]setting in their BIOS while i got nothing in here....
there's 3 solutions i have not tried, 
[LIST=1]
[*]set hdd0 password
[*]> Sometimes the actual name/label is checked, requiring that it be "Windows Boot Manager". Use efibootmgr to change the label from "ubuntuSE" to "Windows Boot Manager" and try booting that. from this [https://ubuntuforums.org/showthread.php?t=2342322](https://ubuntuforums.org/showthread.php?t=2342322)
[*]and the last one is > Either the /EFI/Boot/bootx64.efi got rewritten (from shimx64,efi to grubx64.efi), and/or the nvram entry booting ubuntu got rewritten from /EFI/ubuntu/shimx64.efi to /EFI/ubuntu/grubx64.efi. Take a look and fix the first case by copying the shimx64.efi back to the bootx64.efi. Fix the second case with efibootmgr. Seems someone else just had this problem too. from this [https://ubuntuforums.org/showthread.php?t=2342322](https://ubuntuforums.org/showthread.php?t=2342322) too
[/LIST]

i'll be in touch when i make a progress with this ubuntu 18.04 but i'll stick to win10 for few days.

really miss the old day that i can install ubuntu with no problem like this #-o

---

### Post by oldfred on 2018-05-20
If you just set "trust" which you can only do with an UEFI password which requires, at least temporarily, UEFI Secure Boot be on.

All the other work arounds then are not required, nor recommended for your Acer, since it does work if set correctly.

Another Acer user who just set "trust".
[https://askubuntu.com/questions/1038482/my-bootable-usb-device-does-not-show-up-in-the-boot-order-menu-in-bios-when-i-am?noredirect=1#comment1690910_1038482](https://askubuntu.com/questions/1038482/my-bootable-usb-device-does-not-show-up-in-the-boot-order-menu-in-bios-when-i-am?noredirect=1#comment1690910_1038482)

---

