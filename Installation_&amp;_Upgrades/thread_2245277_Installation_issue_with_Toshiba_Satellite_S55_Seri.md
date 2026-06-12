---
title: "Installation issue with Toshiba Satellite S55 Series"
date: 2014-09-22
forum: Installation &amp; Upgrades
---

### Post by Critical24 on 2014-09-22
Hey guys and girls,

Fast question maybe. I have a Toshiba S55 series, it is the i7 with 12 gigs of ram. I can get it installed with a little work but after I get it installed I have to reboot and when I do that I get a message that says that it can not find the OS and asks me to reinstall it. Any ideas on whats going on with that? I would really like to get this up and running so when I go to the Microsoft conference on Thursday I can have my distro up and running compared to running Windows 8.1 that came preinstalled on it. 

[http://www.toshiba.com/us/computers/laptops/satellite/S50/S55-A5169](http://www.toshiba.com/us/computers/laptops/satellite/S50/S55-A5169) is the model laptop that I have. Any help would be great thank you.

---

### Post by oldfred on 2014-09-22
Did you install in UEFI or BIOS mode.
Did you erase Windows and just install Ubuntu?

May be best to see details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Some other Toshiba, some require you to copy grubx64.efi into /efi/boot and rename to bootx64.efi. Then in UEFI boot hard drive entry.


 TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)

---

### Post by Critical24 on 2014-09-22
Old Fred,

Thank you I will check into these today. I have backed up all my data and I am ready to rock and roll

---

