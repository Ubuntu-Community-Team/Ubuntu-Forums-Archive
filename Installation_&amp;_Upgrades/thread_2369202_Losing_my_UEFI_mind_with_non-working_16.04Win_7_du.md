---
title: "Losing my UEFI mind with non-working 16.04/Win 7 dual boot"
date: 2017-08-19
forum: Installation &amp; Upgrades
---

### Post by Seamless in Northampton on 2017-08-19
Spent the better part of today going in circles. I am beginning to hate anything containing the letter U, E, F, and I. Had a non-UEFI system with 16.04LTS. Got all new hardware. Installed Windows 7 via UEFI/GPT. 

Trying to install a fresh 16.04 via UEFI to make a dual boot system. Successful install, it seemed, but when I boot up, it goes straight to Windows. No GRUB. Can't get Boot Repair EFI USB to do anything (blank screen after initial screen). Reinstall did nothing. I've tried many things, but all seemed to run afoul of the the UEFI system and not work.

I can still boot into my old Ubuntu if I turn on Legacy boot on the new board.

How can I get the system to recognize GRUB on the UEFI drive and do its thing? 

I've read and read and read, and not found my answer. Though I've found many entries for people who get Ubuntu to work and can no longer boot Windows! My problem is other way round.

THanks!

---

### Post by Seamless in Northampton on 2017-08-19
And all I had to do was post this, apparently, and I got something to work. Turns out my BIOS has an OS boot priority setting. Just had to switch it to Ubuntu there. SMH...

---

### Post by Seamless in Northampton on 2017-08-19
Maybe someone else can find a solution if I post the motherboard: MSI Gaming B3

---

### Post by oldfred on 2017-08-20
I think the mistake was installing Windows 7 in BIOS mode on very new UEFI hardware.
Windows 7 can be converted to an UEFI installer, but has to be copied to a flash drive and a few files moved around.
Windows only boots in BIOS boot mode from MBR partitioned drives.
Windows only boots in UEFI boot mode from gpt partitioned drives.

Ubuntu does not care and UEFI lets you choose how you boot install media UEFI or BIOS and will then Ubuntu will install in that boot mode, which may not be compatible with Windows.

 MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)
[http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387](http://ubuntuforums.org/showthread.php?t=2271540&p=13260387#post13260387) 

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
See also link below on lots more UEFI info.

       
 How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Convert Windows 7 install to UEFI This user said he need the repair/recovery from his Windows 8 to convert Windows 7
[http://ubuntuforums.org/showthread.php?t=2304736](http://ubuntuforums.org/showthread.php?t=2304736)

---

