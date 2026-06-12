---
title: "Ubuntu won't load"
date: 2016-10-13
forum: Installation &amp; Upgrades
---

### Post by agaudet on 2016-10-13
Hello everyone,

Thanks in advance for any help.

I have a new computer (windows10 preinstalled) and I tried to dual boot the system with Ubuntu 16.04 Lts 64 bit version. I have partitioned the hard drive, ran the installer and successfully finished the process. No errors, flags or any other indicator something went wrong during the process.

As instructed by the system I rebooted the computer expecting it to boot with grub and options for Ubuntu or Windows.... Instead it only goes to Windows and boots up automatically. The computer doesn't even recognize that there is a second OS for me to choose from. But if I use the live CD it will see the various partitions and Ubuntu.

My attempts to troubleshoot are as follows:
- checking the BIOS firmware for boot options
- disabling the secure boot option
-disabling the fat start up for Windows
- running live CD and running boot-repair in Linux
- checking that there was a efi partition already
- reinstalling Linux using the manual setup
- reinstalling Windows than Linux
- scoured various websites for anyone with this issue; without success.

Past this I don't know why it won't see Linux or why it won't boot. Any help would be appreciated. 

Note: windows works just fine, so I am pretty sure it's not the source of heartaches.

---

### Post by ubfan1 on 2016-10-13
What machine/model do you have (they all have their little quirks)?  Do you see "ubuntu" as a choice in the EFI menu (some function key at power-on) to allow boot choice of device/OS -- maybe have to choose hdd first, then get the Windows/ubuntu choice)?  If you post the output of boot-repair and provide link here that will save some questions.

---

### Post by ajgreeny on 2016-10-13
See Boot-Repair in my signature below and follow the instructions there to run the Boot-Info-Script.

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by agaudet on 2016-10-14
to ubfa1: 
I have a Acer aspire TC710. the BIOS is R01-A1. I Don't have a "Ubuntu" choice in the EFI menu to choose from or any other boot option to choose from other than the windows. Not sure what you mean about choosing HDD, can you elaborate more?

to ajgreeny: 
I have not run the boot repair yet as I just finished working my shift and its almost midnight now. however I did look at your boot-repair instructions and I can say with certainty I recognize your page from researching the other day. I did write down the pastebin url from one of my earlier attempts. Here it is: [http://paste2.org/BGaO5e4d](http://paste2.org/BGaO5e4d)  I wrote it down case sensitive as printed by the pastebin. just as a note. I did run the boot-repair in both "recommended settings" and in "advanced option". I can't remember if this url is from one or the other.

---

### Post by ajgreeny on 2016-10-14
Ah, an Acer machine, some of which demand you jump through a few hoops to get anything other than Windows to boot.  I can only point you to these suggestions as I no longer have Windows to worry about, and my computer, though UEFI, does not have non-standard UEFI firmware.

Below is a quote from the thread at [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295) mentioning this problem.

> Systems that only boot Windows from UEFI.
Per UEFI standard you should be able to boot any entry in UEFI boot menu. But some vendors have modified UEFI code to only boot the Windows efi file. The UEFI looks for the Windows file name and only boots it. (Note for Acer, it requires "trust" settings in UEFI)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI with the 64bit version with secure boot on. A few systems will only boot with UEFI and secure boot on or with CSM (BIOS) if secure boot is off. Best to test system to see which modes it boots in. In secure boot mode it will only show/allow systems that have secure boot. You may have to change UEFI settings or set password to allow other devices to boot.

> All Acer require supervisor password & enable "trust" on Ubuntu/grub efi files.
More details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)

---

### Post by RobGoss on 2016-10-14
**Ajgreeny** posted some great information about getting Ubuntu to boot on Acer try to follow the link he posted. I have one Acer that gave me a lot of trouble to get Ubuntu installed so I had to use a different approach 

I used refind boot manager running off a USB with out any problems, here's the link you can read up on it if you like
[http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html)

---

