---
title: "Ubuntu 16.04 64 bit install works; first boot hangs with blinking cursor"
date: 2016-07-28
forum: Installation &amp; Upgrades
---

### Post by dawnroselyn on 2016-07-28
Attempted a Ubuntu 16.04 installation on my MSI gaming PC (Nvidia 765 graphics).  BIOS is in legacy/UEFI mode, so that either technology can be used.  Install DVD booted fine, installation appeared to complete normally (but with an initramfs tools post install script error that I believe is unrelated).  Attempting to boot into the new installation yields a cursor which quickly advances one line (as if someone pressed enter) then blinks.

My original intention was to install Ubuntu onto a second hard drive such that I could use the bios boot selector to switch between Windows 10 and Ubuntu.  I tried the installation again with all other drives removed, and still see the same behavior.

I read that Nvidia cards could sometimes cause this problem, and attempted to hold down shift during boot to pull up the grub menu.  No menu appeared despite repeated attempts.  I then booted into the liveCD, opened a term, set up a chroot environment in the new installation (with dev, etc. mounted), made changes to /etc/default/grub adding the nomodeset kernel parameter, then ran update-grub to write the configuration.  This appeared to complete normally, but the blinking cursor problem persisted.

Note that Ubuntu 14.(something) ran on this computer in a dual boot configuration alongside Windows 10.

Am I dealing with a BIOS/UEFI problem or an Nvidia problem?  What else can be going on?  Why can't I access the grub menu?

---

### Post by ajgreeny on 2016-07-28
I am not sure from your post if you installed Ubuntu in BIOS or UEFI but try tapping Esc quickly and repeatedly instead of Shift at boot and you may get the grub menu to appear.

If so, hit "e" on the keyboard to edit the boot entry, search for the two words **quiet splash** and add **nomodeset** after them, with a space before and after, then hit F10 to boot.  Hopefully that will get you to a low resolution desktop, but from that you should be able to get to Additional Drivers and install the recommended driver for your nvidia card.

---

### Post by oldfred on 2016-07-28
Depending on verisons of MSI gaming or Ubuntu some additional boot parameters seem to be required.

 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

---

### Post by dawnroselyn on 2016-08-01
Thanks for your replies.

> **ajgreeny said:**
> I am not sure from your post if you installed Ubuntu in BIOS or UEFI but try tapping Esc quickly and repeatedly instead of Shift at boot and you may get the grub menu to appear.

If so, hit "e" on the keyboard to edit the boot entry, search for the two words **quiet splash** and add **nomodeset** after them, with a space before and after, then hit F10 to boot. Hopefully that will get you to a low resolution desktop, but from that you should be able to get to Additional Drivers and install the recommended driver for your nvidia card.

tapping Esc quickly and repeatedly yields no results.  The grub menu never comes up no matter what I do.  My intention was to install ubuntu in legacy BIOS mode on a separate physical disk in the PC and use the BIOS boot menu to select which operating system I wanted to run - the default of Windows 10 UEFI on /dev/sda or ubuntu in legacy BIOS mode on /dev/sdc.  I really don't want Windows to be aware that I have Linux on the system in any way, and didn't want to use the Windows UEFI system to decide which OS to boot.  I have since read that if one is using Windows UEFI on the system, it is best to install Ubuntu in UEFI mode, but I'm not clear on why.  Is this advice given on the assumption that the desired end goal is to use the windows UEFI boot system to switch back and forth between OSes?

I tried a clean reinstall with no disks in the computer except for /dev/sdc.  The installation seemed to complete normally but the problem persisted- blinking cursor only when attempting to boot.  I booted up into boot-repair and pulled a report to try to gather more details.  I did discover that /dev/sdc seemed to have no boot loader installed anywhere.  /etc/boot/grub.cfg is also missing.  I'm not sure if grub is set up at all.

Do I need to be trying to get Ubuntu working in UEFI mode?  If so, why, exactly?


> **oldfred said:**
> Depending on verisons of MSI gaming or Ubuntu some additional boot parameters seem to be required.

 [SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[http://ubuntuforums.org/showthread.php?t=2296878](http://ubuntuforums.org/showthread.php?t=2296878)
MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387)
Recommended "libata.force=noncq"
[http://ubuntuforums.org/showthread.php?t=2298912](http://ubuntuforums.org/showthread.php?t=2298912)

Thank you, but none of these circumstances seems to fit.  I'm using an older MSI Z87-GD65 gaming desktop with a i4770 CPU.

---

### Post by oldfred on 2016-08-01
I missed that it was an MSI motherboard not an MSI laptop.
 Disable MSI Z87 fast boot to get it to work
[http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725](http://ubuntuforums.org/showthread.php?t=2272131&p=13258725#post13258725) 

You do not want Windows UEFI to manage booting Ubuntu. But with both systems in UEFI mode then you can set default to boot Ubuntu and grub can boot Windows.
UEFI & BIOS are not compatible, so the only way to dual boot is from UEFI boot menu or one time boot key like f10 or f12.

Post link to report from Boot-Repair.

If you partitioned in advance, with UEFI you must have an ESP on drive seen as sda for grub to install. If in BIOS mode on gpt partitioned drive, you must have a 1 or 2MB unformatted partition with the bios_grub flag. 

I only partition with gpt and add both partitions on every new or totally reformatted drive and even larger flash drives. I started that before UEFI became the standard. But Windows only boots with UEFI from gpt and my very old XP long since retired, would not even see my first gpt drive.


 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

