---
title: "Can't boot into Windows 7 partition after dual boot installation"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by FreeRangers on 2013-06-02
m trying to set up a dual boot on a UEFI ASUS GV75 laptop. I have 2 drives a SSD with the windows EFI partition and windows OS on it, I also have a SATA drive with data and some programs installed on it. 

I removed the SSD from my computer before I installed ubuntu.
 I want to install Ubuntu on the SATA partition. I use Windows to shrink the SATA drive. I boot to the ubuntu disk and set up my partitions (a 300 mb partition for Ubuntu EFI, a 25 GB partition for swap space, and a 300gb EXT 4 root partiton).

Ubuntu installs fine, and I am able to boot to ubuntu, so I put the SSD back in my computer. But when I try to boot to Windows the computer just reboots, then boots into Ubuntu. I don't know how the Windows boot manager got messed up since I took out the SSD before installing Ubuntu.

After som eresearch I found this guide:  [http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610) (particulary the 6th post), but after running boot repair, the ubuntu boot loader added the windows boot manager, but when I select it it gives an error saying that the boot manager is missing, and still fails to boot into windows.

So I'm at the point now where I did a restore on my computer and am back to just windows 7, but I would like to get ubuntu and windows working in harmony together. Any suggestions?

Thanks.

---

### Post by FreeRangers on 2013-06-05
Ok, so the problem seems to be something that happens when I install to the Sata hard drive (this sata hard drive does have some files installed on it (like office, and steam, etc...)). I installed ubuntu to an external hard drive just to test and I am able to boot into both operating systems successfully (except Ubuntu is kind of slow running of the external USB drive). So I don't really want to kepp ubuntu on the external drive, I'd prefer to partition off some space for it on the SATA drive, but when ever I do that it messes up windows. I'm at a bit of a loss here, as I don't know what I need to do to proceed.

---

### Post by fantab on 2013-06-05
Post the '**BootInfo Summary**' that Boot-Repair tool generates and post the link here.

If your SSD is pre-installed then know that some OEM's use SSD in RAID mode and use the SSD for cacheing. To boot Ubuntu in RAID mode requires a different approach. Check in your BIOS to see what SATA Mode is enabled.
Also, if you have 'Intel SRT' then you have to disable it.

Its very difficult to diagnoze the issue without 'BootInfo Summary'.

---

### Post by FreeRangers on 2013-06-05
The SSD isn't OEM, everything (including Windows was intstalled after market)
The SATA Controler is in IDE mode
I couldn't find Intel SRT, so I'm going to assume I don't have it.

Here are the results of the boot-repair:

Results of initial boot-repair (Windows SSD isn't installed)
[http://paste.ubuntu.com/5737631/](http://paste.ubuntu.com/5737631/)

So I continued to follow the directions in the link in my first post.

I reinstalled the Windows SSD and booted in Ubuntu and ran boot-repair again.
This time a message came up and said EFI Detected. Please check the options. I clicked OK. Here's the boot-repair summary:
[http://paste.ubuntu.com/5737691/](http://paste.ubuntu.com/5737691/)

Results of Recommended Repair:
[http://paste.ubuntu.com/5737707/](http://paste.ubuntu.com/5737707/)

I reboot the computer and the ubuntu boot loader looks like this:
Ubuntu
Advanced options ofr Ubuntu
Windows UEFI bkpbootmgfw.efi
Windows boot UEFI loader
Windows UEFI bkpbootmgfw.efi sdb5
Windows boot UEFI loader sdb5

If I choose Windows UEFI bkpbootmgfw.efi or Windows UEFI bkpbootmgfw.efi sdb5 I get this error:
Error: no such deviceon BC-11FE2A
Error: file '/EFI/microsoft/boot/bkpbootmgfw.efi' not found
Press any Key to Continue

If I choose Windows boot UEFI loader or Windows boot UEFI loader sdb5 I get this error:

Error: file '/EFI/microsoft/boot/bkpbootx64.efi' not found
Press any Key to Continue

---

### Post by fantab on 2013-06-06
Your /dev/sda is using GUID Partition Table, GPT but your /dev/sdb is NOT. 
> 
Model: ATA OCZ-AGILITY3 (scsi) 
Disk **/dev/sda: 240GB **
Sector size (logical/physical): 512B/512B 
**Partition Table: gpt**


Model: ATA ST9750420AS (scsi) 
Disk** /dev/sdb: 750GB** 
Sector size (logical/physical): 512B/4096B 
**Partition Table: msdos**

If Windows is installed on /dev/sda then it is booting in UEFI mode but the OS on /dev/sdb is NOT. 
To be able to successfully dual-boot with UEFI we need both the OS to be installed in UEFI mode. And to Boot in UEFI, GPT is a pre-requisite.

Make sure you can boot Win7, if not do a Widnows repair and fix it.

You will have to change the partition table on /dev/sdb to GPT. ***This WILL remove all partitions and the DATA on it. BACK UP ALL YOUR DATA first.
After creating the new GUID partition table using Gparted, create the first partition as:
/dev/sdb1 300MB FAT32 and put a 'Boot' flag on it. This partition will be use for EFI boot.

Ubuntu MUST be installed in UEFI mode only. And GRUB must be installed on /dev/sdb only

---

### Post by darkod on 2013-06-06
First, having the SATA mode in IDE is a real blow to the speed, especially for the SSD. You should have changed it to AHCI before installing win7, because it gives you issues if you try to change it later.

Second, and maybe more important, on UEFI systems there should be only ONE EFI partition as far as I know. If that is true, you CAN NOT remove the SSD when installing ubuntu because the EFI grub files need to go to the same EFI partition.

EDIT: As for the partition tables, that's not a real problem. sda has gpt because windows can work in uefi only on gpt. Ubuntu can work on either combination of legacy boot/uefi and msdos/gpt tables. So, the table on sdb can be msdos and ubuntu to be installed in uefi mode too.

---

### Post by FreeRangers on 2013-06-06
I'm a bit confused here. It seems like Darkod and fantab are saying different things.

Fantab: "Ubuntu MUST be installed in UEFI mode only. And GRUB must be installed on /dev/sdb only"

Darkod: "Second, and maybe more important, on UEFI systems there should be only ONE EFI partition as far as I know. If that is true, you CAN NOT remove the SSD when installing ubuntu because the EFI grub files need to go to the same EFI partition.

As for the partition tables, that's not a real problem. sda has gpt because windows can work in uefi only on gpt. Ubuntu can work on either combination of legacy boot/uefi and msdos/gpt tables. So, the table on sdb can be msdos and ubuntu to be installed in uefi mode too."

Darkod is saying Ubuntu can be installed in either UEFI or legacy boot and GRUB needs to go on the EFI partition, which Would be the windows EFI partition on sda. But then Fantab is saying Ubuntu can only be installed in UEFI mode and GRUB needs to be on sdb

---

### Post by darkod on 2013-06-06
GRUB is not installed to any MBR of any disk in uefi mode. In other words, it will not be installed on /dev/sdb in any case. Unless you used manual install and told it to install on /dev/sdb in which case it might install there (I haven't checked), but it will not be used.

UEFI boot works in different way, so both windows and ubuntu don't install a bootloader to the MBR of any disk. If you look in the second bootinfo link you posted in post #4, with the SSD connected, it clearly says there is no bootloader on sda, the SSD. Yet, windows was booting just fine before the ubuntu install. That's because UEFI systems boot from the EFI partition, not from any MBR of any hdd present. That's why you need to have only one EFI partition so that all OSs have their boot setup there.

Ubuntu must be installed in uefi mode too, to have a uefi dual boot, but that doesn't mean the table needs to be gpt. This is true only for windows. Ubuntu should install just fine on msdos disk in uefi mode.

---

### Post by FreeRangers on 2013-06-06
darkod, so what your saying is I should reinstall Ubuntu but leave the SSD in while I'm doing the install and have the Ubuntu EFI on the same partition as the Windows EFI (on the SSD)?

---

### Post by darkod on 2013-06-06
Yes. But there is no such thing as "ubuntu efi". There is only one efi partition and the ubuntu installer will find it and use it for the bootloader files. You don't create another efi partition yourself.

---

### Post by oldfred on 2013-06-06
Darko,
Have you seen someone boot Ubuntu in a MBR(msdos) drive from an efi partition on another drive? I have always suggested to have both drives be gpt and both installs be UEFI. 
Some have Windows in UEFI on one drive and Ubuntu on another drive in BIOS with MBR or gpt partitioning. But UEFI & BIOS write system info differently for system to use. The Ubuntu install is really the same whether UEFI or BIOS, but grub-efi for UEFI and grub-pc for BIOS are different, so I do not know if it really is grub telling the kernel which mode to use?
When installs are not the same, I thought the only way to dual boot was to go into BIOS and turn on BIOS mode to boot a BIOS install or go into UEFI turn off BIOS and boot in UEFI mode. Some seem to have auto settings, but not sure how they work.

You only can have one efi partition per hard drive, but can chain load from one to another.
       Two Drive UEFI installs
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by FreeRangers on 2013-06-06
I think I understand now. What your saying is currently my Ubuntu is on a hard drive that created with an msdos partition, and that is where the boot loader for ubuntu is. But that msdos partition dosen't know what to do with the UEFI windows boot loader because it is on msdos and not the GPT partition. 

So my options seem to be:
Reinstall Ubuntu and tell it to install the boot loader on the GPT EFI partition on the Windows SSD (sda), this way both the windows and ubuntu boot loaders will be on the gpt partition

or Repartition the sdb hard drive to be gpt, but if I do that I will loose all data on that drive. I do have a backup of that data, but it is just a windows system image backup, and I don't think I can restore the data on that drive using windows system image restore without windows reformatting and repartitioning the drive.

So, if my line of thinking is right I'd rather have both drives as gpt, but I don't know if I can backup the data and restore it once I repartition the drive and still have that data work in windows.

---

### Post by oldfred on 2013-06-06
I have never done it, and I would have good backups, but you may be able to convert.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by FreeRangers on 2013-06-20
Ok, So I had some time to try this again, so here's what I did:

I left both hard drives in the computer.

I booted the Ubuntu cd in UEFI mode, but the cd never loaded, I would get to the splash screen where I could Try ununtu, install ubuntu, or check disk for defects. If I choose install ubuntu it just hung at a black screen (but this option had worked previously when I removed the SSD with windows on it)

So I rebooted the computer and booted the CD drive in SATA mode, I was able to install ubuntu this way. I choose to not install an ubuntu bootloader, because I could probably manually install one later, the primary concern is booting into windows once ubuntu installs.

Ubuntu finished installing, but I still couldn't boot into windows. I don't get it, this ubuntu install had nothing to do with the boot loader. 

Restored system backup, so now I'm back to square one.

---

### Post by oldfred on 2013-06-20
When you boot Ubuntu with UEFI you get grub menu not the accessibility screen. But many video system need nomodeset to boot. And some systems need other boot parameters. Often different for UEFI than for BIOS.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by FreeRangers on 2013-06-21
I booted the ubuntu install cd in UEFI mode and ran the nomodeset command. I install /boot on the gpt hard drive (the SSD with the windows efi partition on it)
Iinstalled \root and \home and the swap partitions on the SATA drive. Ubuntu installed and boot fine, however Windows still does not. 
I ran boot-repair in hopes that that would fix windows. Now on the ubuntu boot loader screen I see ubuntu
advanced options for ubuntu
windows uefi bkpbbtmgfw.efi
windows boot uefi loader
efi/efi/boot/bkpbootx64.efi

if I choose either of te windows options I no longer get the error I was getting in my previous post, but I get a screen that says windows is loading files and there is a progress bar underneath the text. After a few seconds it goes back to the ubuntu boot loader.

If I choose the efi/efi/boot option I get the error "error: file efi/efi/boot/bkpbootx64.efi not found"

---

### Post by oldfred on 2013-06-22
Was Windows still hibernated or did you not resize Windows from inside Windows using its disk tools? It needs repair after a resize and it normally runs that itself on first boot after a resize.
And if hibernated (Windows 8 is always hiberanted) that makes it more difficult to dual boot.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

You may be able to undo the file rename that Boot-Repair does. Many Windows systems only boot the Windows efi file, so we have to rename the Windows file bkpbootmgfw.efi and make the Windows name really be the grub shim file that has the Microsoft secure boot key. Then you boot grub & grub chainloads the bkp.. Windows file.

If you have to restore the Windows efi file to directly boot Windows.
      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
You can also manually copy this file back into your efi Windows folder.

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

### Post by FreeRangers on 2013-06-22
Windows wasn't hybernating, I disabled that feature. Also secure boot is disabled (it was never enabled in the bios)

I restored the efi backup in boot repair, but that did nothing. I still have the same options and the same things happen when I choose those options. Even before I ran boot repair I tried to get into windows (by pressing esc after and getting to the computer's start up menu) but the same problem happened. Boot repair isn't screwing up the windows boot loader, I think the ubuntu installation is.

When you say " You can also manually copy this file back into your efi Windows folder.
Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation"
What file are you talking about? I see bootmgfw.efi file in C:\windows\boot\efi am I supposed to copy that file somewhere?

Sorry I keep asking stupid questions, but I must be overloking something small.

---

### Post by oldfred on 2013-06-22
I do not know if your bootmgfw.efi is actually the grub shim file from Boot-Repairs rename or the original file. So a copy from the Windows c:\ partition would be the original file for sure.

When booting with UEFI, each boot loader has a folder in the efi partition. They are totally separate and directly boot your system from the UEFI menu. If Windows does not boot from UEFI menu then either it it still the grub shim file (which takes you to a grub menu) or it is just a Windows issue.

Grub easily chain loads or refers back to the Windows efi file in the Windows folder to dual boot. 

But Windows secure boot has greatly complicated the process as some only boot Windows (and Ubuntu) with secure boot on. Some boot with secure boot off. 

And many that only boot Windows with secure boot on also only boot the Windows efi file in the Widows folder (Which is against the UEFI standard and should not happen). This then requires the file renaming as a work around or all these systems would only ever boot Windows which may be the Microsoft goal.

---

### Post by FreeRangers on 2013-06-22
I finally got it working. I had to end up reinstalling windows (because for some reason my backup wasn't working anymore). So I installed a fresh copy of windows and set my sata drive to gpt and installed ubuntu on the sata drive. Ran boot repair and now everything is working. All I have to do now is the tedious task of reinstalling all my stuff on windows. Any a big thank you to Oldfred for being patient and helping me with this issue!

---

### Post by oldfred on 2013-06-22
Glad you got it working. :)

---

