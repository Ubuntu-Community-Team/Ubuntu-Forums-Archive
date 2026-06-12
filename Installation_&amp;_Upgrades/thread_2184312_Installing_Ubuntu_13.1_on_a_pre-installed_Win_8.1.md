---
title: "Installing Ubuntu 13.1 on a pre-installed Win 8.1"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by skhandige on 2013-10-28
I have a new HP Pavilion Touchsmart which came with Win 8 which I upgrade to Win 8.1. I created a partition for Ubuntu, created a USB install disk and installed Ubuntu 13.1. But when I boot it now, it goes to the Windows boot manager which gives me choice between Win 8.1 and Ubuntu 13.1. If I choose Win 8.1 it boots correctly to windows. However if I choose Ubuntu 13.1, it says: 

Windows failed to start. 
File: \NST\AutoNeoGrub0.mbr 
Status: 0xc000007b  
The application or OS could not be loaded because a required file is missing or contained errors

I create and ran it with a Ubuntu boot repair disk and the following URL was generated: [http://paste.ubuntu.com/6319489/](http://paste.ubuntu.com/6319489/)

Please help

---

### Post by uaw1998@yahoo.com on 2013-10-28
go here
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by oldfred on 2013-10-28
Know nothing about EasyBCD, but with UEFI it is not required and just adds another level of complexity to an already complex process.
With BIOS boot some used EasyBCD to keep Windows boot loader in MBR, but with UEFI all boot loaders exist side by side in the efi partition and you can choose any at any time from UEFI menu or your one time boot key.

You show signed kernels installed so you should be able to boot directly from UEFI menu even with secure boot on. Do you have an ubuntu entry in UEFI menu or one time boot key?

---

### Post by skhandige on 2013-10-29
I do not have my laptop with me right now to check, but how do I get a  one time boot key? Does Ubuntu 13.1 come with signed kernels by default  and how can you tell?

---

### Post by oldfred on 2013-10-29
How you boot install flash drive is how it installs. With Ubuntu you can install UEFI with secure boot, UEFI without secure boot, and BIOS/CSM boot modes. 
This has made it more confusing as before you only had BIOS boot mode.

 line 301 inb your boot info report
linux	/boot/vmlinuz-3.11.0-12-generic.efi.signed


On my system it is f12, you may have to read manual.
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by skhandige on 2013-10-29
I ran boot-repair with advanced options on it and now when I boot, I am presented with a long list of options (many of them have paths to different EFI files) including those for booting Windows and Ubuntu. It again boots fine to Windows but if I try booting to Ubuntu it flashes a few messages and the last message I see is "Starting LightDM manager" and then the screen just goes blank.

The boot summary URL is [http://paste.ubuntu.com/6325276/](http://paste.ubuntu.com/6325276/)

Thanks for your help.

---

### Post by oldfred on 2013-10-29
Boot-Repair did the rename for those systems that will only boot Windows. It renames the shim to have the Windows name as that may be hard coded into the UEFI. If you can boot Ubuntu directly from UEFI then you do not need rename.
       
Line 1215 in your report
Save and rename /mnt/boot-sav/sda7/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi (/mnt/boot-sav/sda7/boot/efi/EFI/Microsoft/Boot/bkpbootmgfw.efi)
cp /mnt/boot-sav/sda7/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/sda7/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi

      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 

Boot-Repair sees all the .efi files that HP included in efi partition, so it adds entries for all of them. You can backup 25_custom and edit out the ones you do not need. More info in link in my signature.

What video chip do you have. Often nomodeset works, but many newer Intel chips need different boot parameters.

      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by skhandige on 2013-10-30
I am almost there! At the grub setting, I used "Advanced Options" and then got into the grub edit page hitting the "e" key and set nomodeset. It then boots correctly and I made this a permanent entry in grub.

However, I edited /etc/grub.d/25_custom and removed all those EFI entries that are not needed but still see those when I reboot. Any ideas?

Thanks a lot for all the help oldfred, really, really appreciate it :)

---

### Post by skhandige on 2013-10-30
Nevermind, I did not update grub after editing out those lines. I did that and now see only the requires entries in the grub menu screen. Thanks for all the help, please mark this as closed.

---

