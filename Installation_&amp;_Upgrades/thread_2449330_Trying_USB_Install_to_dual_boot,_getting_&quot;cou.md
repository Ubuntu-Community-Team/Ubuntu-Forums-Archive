---
title: "Trying USB Install to dual boot, getting &quot;couldn't allocate usb_device&quot;"
date: 2020-08-24
forum: Installation &amp; Upgrades
---

### Post by n0vaes on 2020-08-24
Hi,

I'm new to Linux, and I am trying to install Ubuntu and failing miserably. I've got "couldn't allocate usb_device" error, and my keyboard and mouce is disabled (both usb too). After this it gets to a command line asking for a liveserver site address so it can continue the install, but I don't have it.

I've been looking around for hours about this, and some people said it's the UEFI system, but I can't disable it. Also tried different pendrives, usb ports, etc.

Really out of ideas here, need some help :(

---

### Post by oldfred on 2020-08-24
What brand/model system? Some need settings.
What video card/chip? Some need settings or safe boot option.
What tool are you using to create live installer flash drive?

Have you updated UEFI from vendor?
And if SSD, updated the SSD firmware?

You need to change drives in UEFI settings from RAID or Intel RST to AHCI.
And turn off Windows fast start up.
You want to keep UEFI on, but may want UEFI Secure Boot off.
Only use Windows to shrink the NTFS partition to make unallocated space for Ubuntu.

See link in my signature below, for more details & links to explain even more info if desired.

Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) & 
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

---

### Post by n0vaes on 2020-08-25
> **oldfred said:**
> What brand/model system? Some need settings.
What video card/chip? Some need settings or safe boot option.
What tool are you using to create live installer flash drive?

Have you updated UEFI from vendor?
And if SSD, updated the SSD firmware?

You need to change drives in UEFI settings from RAID or Intel RST to AHCI.
And turn off Windows fast start up.
You want to keep UEFI on, but may want UEFI Secure Boot off.
Only use Windows to shrink the NTFS partition to make unallocated space for Ubuntu.

See link in my signature below, for more details & links to explain even more info if desired.

Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) & 
[https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)
Easy way to create UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi) 
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

Thank you for the tips! I'll start to check it now.

1- My system is an AMD Ryzen 2200G/Asus EX-A320M-Gaming/NVIDIA 1060 6GB.
2- I used Rufus to create the boot flash drive
3- Its SSD, and it is up to date acording to Kingston's SSD Manager (It's a A400 480GB)

---

### Post by oldfred on 2020-08-25
With Rufus you want to use UEFI/gpt option.
The CSM/Legacy/MBR is for old BIOS systems.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

The Ubuntu live installer ISO is configured when written to flash drive or DVD is for both BIOS & UEFI boot. But the tools have to configure it. Rufus seems to only do UEFI or only BIOS when you use it.
And then if for both, you will get two boot options in UEFI menu for flash drive. One clearly UEFI and one just name/label of flash drive which is then the BIOS/Legacy/CSM boot mode.

---

### Post by n0vaes on 2020-08-25
Yep... rufus was running MBR... I'm about to try it again, also disabling fast boot fom the bios.

I tried to disable secure boot but I couldn't. Will try again.

---

### Post by oldfred on 2020-08-25
Many systems do not call it Secure Boot.
Mine says "Windows" or "Other" and since older says use "Other" for Windows 7.
Windows 7 did not support Secure Boot, so that is really the Secure Boot on/off setting.

---

### Post by n0vaes on 2020-08-25
Sorry to keep bothering you, but I'm still having trouble, even after the suggested changes.

[https://imgur.com/a/0k0B1HK](https://imgur.com/a/0k0B1HK) (Sorry about the image quality, my smartphone is dying. Also, sorry for the ptbr rufus' language)

Here's some screenshots of what I changed. Tried installing a few more times, and each time it froze on the panic error. When I select the UEFI usb flash drive to run, it opens a black screen with ubuntu/ubuntu safe mode. Neither worked, unfortunately.

Rufus default is on MBR, I created the new flash boot on GPT option.

On windows, I unchecked the fast boot option. Unfortunately the secure boot coudn't be disabled as it is greyed out.

Even with fast boot disabled, the usb ports were off when I selected Ubuntu/Ubuntu Safe Mode on the black screen.

Please, if I can share any other info with printscreens, let me know and I'll upload it.

---

### Post by oldfred on 2020-08-25
You can attach screen shots using the Forum's advanced editor and the paperclip icon.
Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Some systems do not open all the settings unless you also put in an UEFI password.
But never lose that password or you may have a brick. Some just reset to blank when done making changes.
Also many UEFI systems have USB settings that need changes. Often USB boot is on considered secure as then another can boot system. So you have to turn on allow USB boot or full USB support or similar setting.

May be similar as vendors use same UEFI across multiple models.
Asus ROG Zephyrus GA502 Ryzen 7 3750H + Nvidia GTX 1660 Ti Set up Guide
[https://ubuntuforums.org/showthread.php?t=2440670](https://ubuntuforums.org/showthread.php?t=2440670)

---

### Post by n0vaes on 2020-08-27
> **oldfred said:**
> You can attach screen shots using the Forum's advanced editor and the paperclip icon.
Post #4 1024x768 if photo
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

Some systems do not open all the settings unless you also put in an UEFI password.
But never lose that password or you may have a brick. Some just reset to blank when done making changes.
Also many UEFI systems have USB settings that need changes. Often USB boot is on considered secure as then another can boot system. So you have to turn on allow USB boot or full USB support or similar setting.

May be similar as vendors use same UEFI across multiple models.
Asus ROG Zephyrus GA502 Ryzen 7 3750H + Nvidia GTX 1660 Ti Set up Guide
[https://ubuntuforums.org/showthread.php?t=2440670](https://ubuntuforums.org/showthread.php?t=2440670)

I finally done it! Needed to update bios. Researched and they made changes for it, updating UEFI system.

Thank you very much for being so supportive! Really appreciate the time you took to help me. Cheers!

---

