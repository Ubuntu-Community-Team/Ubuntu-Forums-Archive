---
title: "What do I answer for &quot;Device for Boot Loader Installation&quot; UEFI"
date: 2016-01-13
forum: Installation &amp; Upgrades
---

### Post by svref on 2016-01-13
Objective:
Convert UEFI Windows 10 laptop to a  dual boot system using "something else" install path 

Ubuntu 14 dvd installer couldn't sense the existence of Windows 10, so it was either "something else" or "wipe out Windows and take over the whole machine"

The story so far:
I have shrunk the biggest partition to free up some space using the ubuntu installer's partition thing:
Here's a picture of [before]("https://goo.gl/photos/JXA1Cnpxfb1ajBRm7") and [after]("https://goo.gl/photos/5HJKph6b98eU7MJ57") 


Note: UEFI somehow lives on /dev/sda1, right?

As you can see in the second link, Ubuntu installer now asks for "Device for boot loader installation". I don't know!
Is that /dev/sda - like nearly every pre-uefi guide says?
Is that /dev/sda1 - will it be smart enough to just 'hang out' with the Win10 files there?

---

### Post by Dennis N on 2016-01-13
Whatever you select there is ignored by the installer when installing in UEFI mode. The installer searches for the EFI system partition on sda and installs it there regardless. Bottom line: you can't make an incorrect choice - I just leave it on sda.

---

### Post by grahammechanical on 2016-01-13
I would like to clarify something. You may already know it.

On a machine with a UEFI boot system and Windows 10 pre-installed or upgraded from Windows 8.1 it is most likely that Windows 10 will be installed in EFI mode. That means we should run the Ubuntu live session in EFI mode and then Ubuntu will be installed in EFI mode. Whatever mode one OS is installed in (EFI or BIOS/Legacy) the other OS must also be installed in. If we do not do that then we will only be able to load one of the 2 OS.

If Windows is installed in EFI mode and the Ubuntu live session is running in BIOS/Legacy mode, then we will only get the option to Erase disk & install Ubuntu or Something Else. No offer to install alongside.

If Windows 10 is installed in EFI mode then the Windows installer will have created an efi boot partition for the Windows efi boot files. The Ubuntu installer when installing Ubuntu in EFI mode will make use of the existing efi boot partition to put the Ubuntu efi boot files in and it will do that without over-writing the Windows efi boot files. And sda1 will be the efi boot partition.

I am guessing that the Ubuntu live session is running in BIOS/legacy mode. If it is running in efi mode then there can only be one place to install the Ubuntu boot loader efi files - sda1

Regards.

---

### Post by Dennis N on 2016-01-13
> If it is running in efi mode then there can only be one place to install the Ubuntu boot loader efi files - sda1
You get the same choices as with BIOS mode, but in UEFI they have no effect. Case in point: With two disks, if you have prepared an EFI system partition on sdb and select that, it will still install the bootloader to sda if there is an EFI system partition there to use. I don't know what would happen if there was an EFI system partition on sdb but none on sda. Never had a chance to see.

Some installers let you choose the EFI system partition to use: Manjaro's and Fedora's for example.

---

### Post by svref on 2016-01-13
Thanks all for the timely replies!

Grahammechanical, that was particularly helpful. 

Is there any way to run ubuntu live session in EFI mode? Tools I have: 
1. Windows 10 booted in EFI mode with a net connection
2. Ubuntu DVD which I can boot in BIOS mode only,  with no net connection

---

### Post by westie457 on 2016-01-13
Maybe this link will be helpful to you and anyone else having a similar problem.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2016-01-13
You do not want to boot in BIOS mode and then install boot loader to ESP - efi system partition.
And you should have two boot options from UEFI menu. One clearly UEFI:name and the other just name or BIOS boot. Where name is name of flash drive. Not sure what it shows with DVD, as few use that any more. 

You may have to turn off secure boot. And you may have to turn on UEFI boot or allow boot from USB devices or similar setting in UEFI. My Asus motherboard would only boot in BIOS mode even with UEFI & BIOS with UEFI as first. Only the UEFI only setting with secure boot off worked.

---

### Post by svref on 2016-01-14
Thank you oldfred et alles.
I sussed up a SDcard, put Ubuntu onto it, and was able to boot it under UEFI. From there the installer was able to do it's thing. Marking as "solved".

---

