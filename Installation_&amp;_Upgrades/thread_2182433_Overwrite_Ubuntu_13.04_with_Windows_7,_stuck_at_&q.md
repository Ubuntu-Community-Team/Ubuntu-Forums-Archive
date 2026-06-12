---
title: "Overwrite Ubuntu 13.04 with Windows 7, stuck at &quot;starting windows&quot; screen."
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by feedme2ashark on 2013-10-21
After fiddling with the settings in ubuntu 13.04 I found that i needed to downgrade to windows 7. I have the official boot CD's and can get my laptop to boot the CD. My only problem seems to be that it freezes at the "Starting Windows" screen. I' ve done everything from re-aranging my boot order, trying to boot through ubuntu, cleaning the disk itself, trying the 32-bit disk, and even trying to boot from a USB stick( which my BIOS does not support, or at least it never works). I have an Acer Aspire V3-551G. I'm not new to computers, before you ask. When bootin off the disk the only option i get is to launch the windows 7 installer. I've tried to get to the command prompt on the disk, with no avail(I'm going to keep trying). THe disk is not scratched and is in almost perfect condition. Please help! Thank you in advanced.

---

### Post by fantab on 2013-10-21
Windows will not install if there are no NTFS partitions.

Since you want to remove Ubuntu and reinstall Windows, I'd suggest that you reformat the HDD by deleting all partitions, if possible. Re-create the partition table as well.
Do external backups of all your DATA worth saving.

Boot with Ubuntu DVD/USB, 'Try Ubuntu without installing'... Open Gparted, delete all partitions, re-create partitions as need and format them with NTFS.
Boot with Windows disc. Reformat the partitions again with Windows installers Disk Management.

Or the CD you are using could be corrupt.

---

### Post by oldfred on 2013-10-21
You mention downgrade?
If system was Windows 8 you have gpt partitioning and Windows only installs in UEFI mode with 64 bit version from  a flash drive with gpt partitioning. If you have a Windows 7 DVD you have to convert to flash drive ans make changes so it can boot in UEFI mode.

Or you have to totally erase drive and convert to BIOS boot with MBR partitions. If a newer computer running 32 bit lowers performance.

---

### Post by feedme2ashark on 2013-11-15
Sorry for not responding, but i got busy. I have a few points to say:
1) When i say downgrade, I mean that I hate windows and prefer linux and that i am "downgrading" to the lesser OS
2) I have reformatted the drive to the NTFS format, and that doesn't seem to help
3) I can't boot from a flash drive with this laptop, from the research I've done, the BIOS doesn't support it.
4) I haven't been able to open the command prompt, but i have been able to open a screen that allows me to change the windows boot options.
5) I am well aware the 32-bit lowers performance, but i just wanted to check all possible solutions.

---

### Post by oldfred on 2013-11-15
All new computers boot from flash. But some add protection or settings.
You may have to turn secure boot off and Windows 8 fast boot off. 
The Ubuntu 64 bit version will boot in either UEFI or BIOS boot mode from UEFI menu.
Some have passwords in UEFI/BIOS.
Many computers discuss USB booting, but that does not include flash drives. But then flash drives appear as another hard drive in the options of which hard drive to boot, not which USB device to boot.
System will not show a flash drive unless you reboot with a bootable flash drive plugged in and sometimes only certain USB ports may work.

 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)
Acer UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64 June 2012
[URL="http://ubuntuforums.org/showthread.php?t=2003442"]http://ubuntuforums.org/showthread.php?t=2003442

[/URL] Video on getting into UEFI - 1 Min Acer but all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

[URL="http://ubuntuforums.org/showthread.php?t=2003442"]
[/URL]

---

