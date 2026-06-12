---
title: "New Win10 / Ubuntu install process"
date: 2019-11-12
forum: Installation &amp; Upgrades
---

### Post by roberthleeii on 2019-11-12
I am trying to dual boot Ubuntu on my HP laptop with Windows 10 installed. The laptop is a new (late 2019) HP Pavilion x360, i5, 16 gb ram, 256 gb OS drive and 1 tb hard drive. 

  
I ran Ubuntu from the flash drive I made to make sure everything seemed compatible and then rebooted and tried to install from the flash drive. I stopped the install when I got the install location because I was not able to see my 256 gb OS drive where I wanted to install the Ubuntu OS. I canceled the install and booted back into windows. Everything seems to work fine but I decided I wanted to try to install when I run the Try Ubuntu and still could not see the OS drive I wanted to use and canceled. Now everything works in windows, but I cannot even get into the Ubuntu USB I made. I get a critical error when booting to the USB and the computer shuts down. When I turn the computer on again windows works fine but I would still like to get Ubuntu installed beside Windows. I have been doing research to figure out what was wrong, and it seems there are some steps I really need to do before installing Ubuntu with UEFI/windows. 

  
Can anyone help guide me on the correct way to dual boot this machine? And how to fix whatever I messed up causing me to not be able to boot to the USB? 

Robert

---

### Post by oldfred on 2019-11-12
I might recreate flash drive.
Sometimes UEFI/BIOS reset drive order and grub gets installed into flash drive not to install drive.
Also you need to be sure UEFI settings do allow USB boot, and usually best to have fast boot in UEFI off, fast start up in Windows must be off, and UEFI secure boot off.

Lots of potential reasons for flash drive not working. Generally if you use one of the standard methods to create it and have correct settings in UEFI, it just works.
USB boot issues:
[https://askubuntu.com/questions/1186435/why-doesnt-my-bootable-usb-boot](https://askubuntu.com/questions/1186435/why-doesnt-my-bootable-usb-boot)


General UEFI install instructions in link in my signature.

HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)

---

### Post by roberthleeii on 2019-11-12
> **oldfred said:**
> I might recreate flash drive.
Sometimes UEFI/BIOS reset drive order and grub gets installed into flash drive not to install drive.
Also you need to be sure UEFI settings do allow USB boot, and usually best to have fast boot in UEFI off, fast start up in Windows must be off, and UEFI secure boot off.

Lots of potential reasons for flash drive not working. Generally if you use one of the standard methods to create it and have correct settings in UEFI, it just works.
USB boot issues:
[https://askubuntu.com/questions/1186435/why-doesnt-my-bootable-usb-boot](https://askubuntu.com/questions/1186435/why-doesnt-my-bootable-usb-boot)


General UEFI install instructions in link in my signature.

HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)


Thanks for the quick reply. 

I have turned off fast start up and UEFI secure boot but cant find fast boot in UEFI, do I need to enable legacy support?

---

### Post by oldfred on 2019-11-12
My Asus motherboard seems backwards.
I have to go into legacy support to turn on UEFI or legacy.
Fast boot was a totally separate setting, but each vendor enables it somewhat differently.
You have it somewhere as fast boot is required by Microsoft to have system boot faster to make up for the slow boot of Windows.

Fast boot in UEFI assumes no system or hardware change, that previous info written to drive is correct, so it skips scan of system. That skip then is often so quick that you do not even have time to press any keys to get into system or UEFI boot menu. My system has setting for delay. 
Most systems will do full scan on a cold boot or full reboot from power down.

---

### Post by roberthleeii on 2019-11-13
> **oldfred said:**
> My Asus motherboard seems backwards.
I have to go into legacy support to turn on UEFI or legacy.
Fast boot was a totally separate setting, but each vendor enables it somewhat differently.
You have it somewhere as fast boot is required by Microsoft to have system boot faster to make up for the slow boot of Windows.

Fast boot in UEFI assumes no system or hardware change, that previous info written to drive is correct, so it skips scan of system. That skip then is often so quick that you do not even have time to press any keys to get into system or UEFI boot menu. My system has setting for delay. 
Most systems will do full scan on a cold boot or full reboot from power down.

Thank you again for the help. I would be lost with out the guidance. I can boot in to the USB now and "Try Ubuntu". I played in there and everything seems to work when running from the USB. 

I have searched everywhere and cannot find the UEFI fast boot in the BOIS/UEFI menus, is it possible that it is not on this laptop and can I proceed without turning it off? I have turned the others off and enabled legacy boot

When I go to install should I do the normal install where there is the slider to partition and determine where the Ubuntu OS will be installed or is it better to partition the hard drive in Win10 before and have the free space ready and choose the something else option? 

when reading the articles and help documents I noticed that a lot mentioned creating a swap partition. It seems that this would be most helpful for computers with limited RAM, having 16 GB on this laptop I don't see that being an issue. But I saw mention that if there is no swap hibernation would not work or not work well....   Is this something i should worry about?  I want to get this right the first time so I don't have to worry about it again. 

And one more question: should i check the install third-party software option? I would normally click that option but when I installed Ubuntu on an older laptop it mentioned some security settings and I did not know if that had any effect on this Win10/UEFI security/boot stuff....

Thanks in advance,

Robert Lee

---

### Post by oldfred on 2019-11-13
If this in not an old computer, you do not want legacy support turned on.

Did you review the threads specific to HP 360's? They have had some issues and I think most were resolved in various threads.

And review general UEFI install instructions in link in my signature.

---

### Post by roberthleeii on 2019-11-14
> **oldfred said:**
> If this in not an old computer, you do not want legacy support turned on.

Did you review the threads specific to HP 360's? They have had some issues and I think most were resolved in various threads.

And review general UEFI install instructions in link in my signature.

When reading through the different threads some said to turn legacy on and some said to leave it off. I guess I need to re-enable it?

---

### Post by roberthleeii on 2019-11-14
> **oldfred said:**
> If this in not an old computer, you do not want legacy support turned on.

Did you review the threads specific to HP 360's? They have had some issues and I think most were resolved in various threads.

And review general UEFI install instructions in link in my signature.

Is there a difference between changing the boot order to boot from USB and telling it to boot to the USB the one time you want to install it?

---

### Post by roberthleeii on 2019-11-14
> **oldfred said:**
> If this in not an old computer, you do not want legacy support turned on.

Did you review the threads specific to HP 360's? They have had some issues and I think most were resolved in various threads.

And review general UEFI install instructions in link in my signature.

> **roberthleeii said:**
> When reading through the different threads some said to turn legacy on and some said to leave it off. I guess I need to re-enable it?

I changed the setting back to legacy support is disabled and it will no longer boot to the Ubuntu USB

[ATTACH=CONFIG]284403[/ATTACH]

---

### Post by oldfred on 2019-11-14
Many seem to have the mmx64.efi missing error. I have not seen it.
Standard fix is just to copy (anything?) grub64.efi into /EFI/Boot and rename to mmx64.efi.
Once installed you will have the correct mmx64.efi in both /EFI/Boot & /EFI/ubuntu.

The mmx64.efi is used for a user to create a UEFI key. That in required if Secure boot is on & you are installing any proprietary driver like nVidia or Wi-Fi. Ubuntu cannot provide key for proprietary software that it does not create. A user can, but then assumption is that user knows if software is ok for UEFI Secure boot or not.

What software did you use to create Ubuntu live installer onto flash drive? Make sure you have UEFI, not just BIOS or CSM version setting. ISO is for both and should be configured for both, but some software used to create live installer seems to make only UEFI or only BIOS versions.

Can't install Ubuntu 18.10 on XPS 15 9570 - EFI\BOOT\mmx64.efi not found
[https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found](https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found)

Supposedly bug is fixed:
System fails to boot with \EFI\BOOT\mmx64.efi - Not Found
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171)

---

### Post by roberthleeii on 2019-11-14
> **oldfred said:**
> Many seem to have the mmx64.efi missing error. I have not seen it.
Standard fix is just to copy (anything?) grub64.efi into /EFI/Boot and rename to mmx64.efi.
Once installed you will have the correct mmx64.efi in both /EFI/Boot & /EFI/ubuntu.

The mmx64.efi is used for a user to create a UEFI key. That in required if Secure boot is on & you are installing any proprietary driver like nVidia or Wi-Fi. Ubuntu cannot provide key for proprietary software that it does not create. A user can, but then assumption is that user knows if software is ok for UEFI Secure boot or not.

What software did you use to create Ubuntu live installer onto flash drive? Make sure you have UEFI, not just BIOS or CSM version setting. ISO is for both and should be configured for both, but some software used to create live installer seems to make only UEFI or only BIOS versions.

Can't install Ubuntu 18.10 on XPS 15 9570 - EFI\BOOT\mmx64.efi not found
[https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found](https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found)

Supposedly bug is fixed:
System fails to boot with \EFI\BOOT\mmx64.efi - Not Found
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171)

i created it on rufus following the directions linked from the download page on ubuntu.com. I reformatted the usb and am re burning it right now to see if the file is there. 
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.117844169.1188381502.1573687961-1547351887.1573397008#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.117844169.1188381502.1573687961-1547351887.1573397008#0)

I wonder why it was booting when i had it in legacy mode without that file....

---

### Post by oldfred on 2019-11-14
I have never used Rufus, but I think this screen shot is not correct for UEFI.
UEFI has CSM.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.117844169.1188381502.1573687961-1547351887.1573397008#2](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.117844169.1188381502.1573687961-1547351887.1573397008#2)

Most systems will boot in either UEFI or BIOS from MBR or gpt partitioned flash drives. Only a few UEFI/BIOS systems were more particular and wanted one or the other.
Some other methods use dd or some software to make dd a bit less dangerous and that makes a hybrid DVD/flash drive. Flash drive is then not partitioned at all and at least first sectors have to be zeroed out to allow partitioning and reuse. The main issue with dd is that is uses device likr  /dev/sdb. But some BIOS make flash drive sda and internal drive sdb, so then you erase your system, if you have that type of UEFI/BIOS. Most users do not note detail which can be critical.

Make sure in Rufus you select UEFI, not UEFI/CSM and probably gpt partitioning so it defaults to UEFI?

---

### Post by roberthleeii on 2019-11-14
> **oldfred said:**
> Many seem to have the mmx64.efi missing error. I have not seen it.
Standard fix is just to copy (anything?) grub64.efi into /EFI/Boot and rename to mmx64.efi.
Once installed you will have the correct mmx64.efi in both /EFI/Boot & /EFI/ubuntu.

The mmx64.efi is used for a user to create a UEFI key. That in required if Secure boot is on & you are installing any proprietary driver like nVidia or Wi-Fi. Ubuntu cannot provide key for proprietary software that it does not create. A user can, but then assumption is that user knows if software is ok for UEFI Secure boot or not.

What software did you use to create Ubuntu live installer onto flash drive? Make sure you have UEFI, not just BIOS or CSM version setting. ISO is for both and should be configured for both, but some software used to create live installer seems to make only UEFI or only BIOS versions.

Can't install Ubuntu 18.10 on XPS 15 9570 - EFI\BOOT\mmx64.efi not found
[https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found](https://askubuntu.com/questions/1085550/cant-install-ubuntu-18-10-on-xps-15-efi-boot-mmx64-efi-not-found)

Supposedly bug is fixed:
System fails to boot with \EFI\BOOT\mmx64.efi - Not Found
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1798171)

> **roberthleeii said:**
> i created it on rufus following the directions linked from the download page on ubuntu.com. I reformatted the usb and am re burning it right now to see if the file is there. 
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.117844169.1188381502.1573687961-1547351887.1573397008#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.117844169.1188381502.1573687961-1547351887.1573397008#0)

I wonder why it was booting when i had it in legacy mode without that file....

Thanks!!

after remaking the USB it still did not have the file so i copied it. That worked!

Should i make the partition in Win10? and do I need a swap partition?

---

### Post by roberthleeii on 2019-11-14
> **oldfred said:**
> I have never used Rufus, but I think this screen shot is not correct for UEFI.
UEFI has CSM.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.117844169.1188381502.1573687961-1547351887.1573397008#2](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows?_ga=2.117844169.1188381502.1573687961-1547351887.1573397008#2)

Most systems will boot in either UEFI or BIOS from MBR or gpt partitioned flash drives. Only a few UEFI/BIOS systems were more particular and wanted one or the other.
Some other methods use dd or some software to make dd a bit less dangerous and that makes a hybrid DVD/flash drive. Flash drive is then not partitioned at all and at least first sectors have to be zeroed out to allow partitioning and reuse. The main issue with dd is that is uses device likr  /dev/sdb. But some BIOS make flash drive sda and internal drive sdb, so then you erase your system, if you have that type of UEFI/BIOS. Most users do not note detail which can be critical.

Make sure in Rufus you select UEFI, not UEFI/CSM and probably gpt partitioning so it defaults to UEFI?

there is no UEFI only option, There is only one target system option :(

---

### Post by oldfred on 2019-11-14
If you choose gpt, is it then UEFI?

New installs use a swap file, so swap partition is not required.

Only use Windows 10 tools to shrink NTFS partitions. Windows has been known to rewrite partition table and "forget" to include Linux partitions. Data is still there, just missing entry in partition table. Bug since Windows 7 with any major update. Some Windows 10 post recently have shown similar issues with AOMEI partitioning tool.

---

### Post by roberthleeii on 2019-11-14
> **oldfred said:**
> If you choose gpt, is it then UEFI?

New installs use a swap file, so swap partition is not required.

Only use Windows 10 tools to shrink NTFS partitions. Windows has been known to rewrite partition table and "forget" to include Linux partitions. Data is still there, just missing entry in partition table. Bug since Windows 7 with any major update. Some Windows 10 post recently have shown similar issues with AOMEI partitioning tool.
  
If I select GPT then the only target option is "UEFI (non CSM)"

does it make a difference? the drive works after making the copy of the file...

---

### Post by oldfred on 2019-11-14
It sounds like it makes UEFI only or CSM boot flash drive.
Did the version using MBR and CSM also boot in UEFI boot mode or only BIOS/CSM boot mode?

And then copy to create mmx64.efi is required with which version or both?

---

### Post by roberthleeii on 2019-11-17
> **oldfred said:**
> It sounds like it makes UEFI only or CSM boot flash drive.
Did the version using MBR and CSM also boot in UEFI boot mode or only BIOS/CSM boot mode?

And then copy to create mmx64.efi is required with which version or both?

Thank you for all your help. I got Ubuntu and Win10 dual booting on my machine now.

The 3 things I did were: 1) disable fast startup in windows 2) disable secure boot in UEFI 3) Copied the mmx64.efi on the USB stick.  That seems to have everything working fine now.

Robert

---

