---
title: "Unable to install Ubuntu 20.04 on system with Windows 10"
date: 2021-07-20
forum: Installation &amp; Upgrades
---

### Post by davy jones on 2021-07-20
I've recently purchased a Dell Vostro 3500 with Windows 10 pre-installed. It is a UEFI system. I don't want to keep Windows 10 and I want to replace it with Ubuntu 20.04. I followed the regular method as follows:


1. Created a live USB for Ubuntu
2. Changed boot order in BIOS to boot it from the live USB (a note: for some reason it showed two different options in BIOS; both are my live USB)
3. Let the disk check happen to ensure there were no errors


Then the installation process started. At the "Updates and Software" stage, it simply said that Ubuntu requires 8.6 GB of space while my system has only 8.1. It gave no options to continue forward to the point where it gives installation options (installing alongside Windows, erasing it, or something else).

I then learned about BitLocker encryption. My computer doesn't have BitLocker GUI but I went to Device Encryption and turned off the encryption. I checked in Disk Management, using Command Prompt, and on my Microsoft account. All three confirm that my hard disk is no longer encrypted. But the Ubuntu live USB behaviour does not change. It still doesn't even detect my hard disk (I checked using Gparted and Disks in the live session, and the only volume it shows is my USB drive).


What do I do here? Almost all tutorials online say that this is how it is supposed to be done and I can't find any other instances of someone facing this problem.

---

### Post by tea for one on 2021-07-20
> **davy jones said:**
> 2. Changed boot order in BIOS to boot it from the live USB (a note: for some reason it showed two different options in BIOS; both are my live USB)

[COLOR="#0000FF"]UEFI:[/COLOR] (i.e. UEFI with a colon) followed by name of disk i.e. Kingston or Sandisk etc
This means Boot in UEFI mode = Install in UEFI mode

If there is no [COLOR="#0000FF"]UEFI:[/COLOR], then you boot in Legacy mode
You will need UEFI mode [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> **davy jones said:**
> It still doesn't even detect my hard disk (I checked using Gparted and Disks in the live session, and the only volume it shows is my USB drive)

Is Windows 10 in hibernation mode?

Here is a little checklist (not all will apply)

Backup your data
Both systems in UEFI mode with GPT
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

_UEFI settings_

Disable Secure Boot
Disable Fast boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM

[U]Windows 10
[/U]
Backup your data
Turn off Bitlocker 
Do not have any drives encrypted during Ubuntu installation process
Disable Fast Start Up i.e. Windows is not hibernating
Disable applications which manage Intel Optane memory & storage
Disk must be GPT
Install Windows 10 in UEFI mode
Check via System Information > System Summary > BIOS mode > UEFI
Windows will have  an EFI partition (needed by Ubuntu later)
Use Windows tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

_Ubuntu Family_

Boot into a live session in UEFI mode (how you boot determines the installation mode)
Check wifi, sound, graphics, mouse, keypad etc
Install Ubuntu in the free space previously created (or your own partition scheme e.g. separate root and home)
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Grub will find the EFI partition already used by Windows

---

### Post by tea for one on 2021-07-20
Whoops, I just noticed that you wanted to replace Windows completely - A good chunk of my previous post will be redundant.

---

### Post by tea for one on 2021-07-20
Does your new device have 11th Generation Intel Processor?

Ubuntu 20.04 may not have support for this processor in the kernel and you may need a later kernel - try Ubuntu 21.04?

---

### Post by davy jones on 2021-07-21
Thanks, that solves the problem. [Here]("https://ubuntuforums.org/showthread.php?t=2462045&page=2") is another thread which had the same conclusion.

---

