---
title: "device for bootloader installation"
date: 2018-12-14
forum: Installation &amp; Upgrades
---

### Post by grahaml2 on 2018-12-14
Installing Ubuntu on to a second SSD, a few questions.
 
 
 I have W10 installed on one SSD, this is at the moment my operating system.
 I have installed a second unformatted 60gb SSD.
 I have Ubuntu on a USB stick and have booted from it and looked at the installation procedure.  
 I’ve looked at a few at a few forum posts, installation procedures and videos and think :) I know most of what to do. However do have a few questions.  
 
 
 The questions.
 
 
 ‘device for bootloader installation’  do I choose the SSD I'm installing Ubuntu onto or the SSD that contains the W10 installation.  
 This info might be relevant ? the MB is a ‘ ASUSTeK  F2A85-M’ with  UEFI bios
 
 
 Is the UEFI bit important and if so what am I supposed to do or not do regards UEFI

---

### Post by yancek on 2018-12-14
The first thing I would suggest you do is to read the official Ubuntu documentation at the site below on dual-booting with windows UEFI.

[COLOR=#242729][FONT=inherit]https://help.ubuntu.com/community/UEFI

If you want to install Ubuntu to a separate SSD and use UEFI, you have options.  If you plan to have both drives permanently attached, you can boot the Ubuntu installer and install Ubuntu UEFI which will put the Ubuntu Grub boot files in a separate directory in your EFI partition on the windows drive.  You should then be able to access either windows/ubuntu from the Grub boot menu.   If you want the systems totally separate, create a FAT32 formatted partition on the Ubuntu drive prior to the install (2-500MB in size) and proceed with the install.  If you select this method, you should remove the windows SSD before beginning 
[/FONT][/COLOR]

---

### Post by oldfred on 2018-12-14
Many new systems have a setting in UEFI to turn off a drive, so you do not have to open case to only have second drive active.

If you do not disconnect Windows drive, you must manually partition in advance with gpt partitioning and include an ESP as first partition.
Grub will install another folder /EFI/ubuntu into the ESP on Windows drive. It does not matter what you specify during a manual install. I just tried with 19.04 to see if grub was updated and it still overwrote my /EFI/ubuntu folder in my first drive. I unmounted sda's ESP, mounted sdb's ESP, and specified on combo box to use sdb. It still overwrote my ESP on sda. I learned to backup ESP as I install Ubuntu multiple times to multiple drives & flash drives.

Be sure to boot installer in UEFI boot mode. How you boot install media UEFI or BIOS/CSM is then how it installs.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by grahaml2 on 2018-12-20
Hello and thanks

Apology for the delay in getting back to acknowledge answers, i did read, they did *help 
I now have Ubuntu dual booted and the grub is working and W10 isn't screwed :) Happy days

* the UEFI links was both helpful and confusing, the more i know the less i understand - managed to find a YouTube vid that had the same bios as me and showed the correct settings :)

Anyway is now installed and i'm now having fun/pain transferring settings and profiles and such like 
No doubt i'll at some point be starting a few new threads asking 'how do i do whatever'

again thanks

---

