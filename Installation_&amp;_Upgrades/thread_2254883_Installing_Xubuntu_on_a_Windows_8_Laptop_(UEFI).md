---
title: "Installing Xubuntu on a Windows 8 Laptop (UEFI)"
date: 2014-11-30
forum: Installation &amp; Upgrades
---

### Post by cobradabest on 2014-11-30
I'm trying to install Xubuntu on my laptop, which has Windows 8 (UEFI) pre-installed. I'm using a bootable USB with the live daily iso on it. When I try to boot into the usb it says:

"System has no USB boot option"

It then gives me the option to boot into Windows again.

I've tried everything to resolve this, even restoring the PC to factory settings, but nothing worked, hence that I'm here posting this.

What do I do?

If it helps, here are the Specs:
1.6Ghz Intel Celeron CPU
360GB HDD (130GB per partition)
2GB Ram

---

### Post by oldfred on 2014-11-30
If system is new enough to have Windows 8, then it should boot from USB.
But new UEFI systems have lots of settings and may need several changed.
You need to turn off secure boot in UEFI, fast boot in Windows.
And you may need to turn on USB port booting or other settings for USB ports.
Some systems do not let you change some of those settings or even show them unless you also set a password. But never ever lose that password if one is required.

---

### Post by cobradabest on 2014-12-01
> **oldfred said:**
> If system is new enough to have Windows 8, then it should boot from USB.
But new UEFI systems have lots of settings and may need several changed.
This what I don't understand, I successfully install Ubuntu on the very same laptop at one point by using the exact same method, but then I tried installing Linux Lite over it, but it mucked the whole thing up!

> **oldfred said:**
> You need to turn off secure boot in UEFI, fast boot in Windows.
I've been trying to find that option for some time now, but I never saw it anywhere... Do you by any chance know where I could find it? 

> **oldfred said:**
> And you may need to turn on USB port booting or other settings for USB ports.
Some systems do not let you change some of those settings or even show them unless you also set a password. But never ever lose that password if one is required.
That might play a role in my problem, and I'm sure I know the password to use for them, but I don't think I ever came across anything in any options or menus that asked for one...

---

### Post by oldfred on 2014-12-01
You did not mention brand/model. It varies.
Screenshots of secure boot settings Asrock, Asus, HP, Acer
[https://neosmart.net/wiki/disabling-secure-boot/](https://neosmart.net/wiki/disabling-secure-boot/)

    
 Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

On my new motherboard, they did not call it secure boot, but had a setting for Windows & 'other'. Which I assume is secure boot.

---

### Post by cobradabest on 2014-12-01
I'm using a Packard Bell laptop, who are now a division of Acer, so I followed the instructions on the link you provided, and disabled security boot, but it still gives me the same error...

---

### Post by oldfred on 2014-12-01
With secure boot off, are there any settings for USB ports enabling?

There were/are a few 32 bit systems that were designed to prevent anything but Windows from installing. 
This is not one of those, is it?

       Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)
Packard Bell ENME69BMP InsydeH2O  or Gateway LT41P04u
32-bit UEFI Support Proposed For Ubuntu Linux
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE)
Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
But someone has it partially working:
[http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)

---

### Post by cobradabest on 2014-12-02
> **oldfred said:**
> With secure boot off, are there any settings for USB ports enabling?
Only for USB FDD, USB CD-ROM and USB HDD, but none about booting from a USB itself.

> **oldfred said:**
> There were/are a few 32 bit systems that were designed to prevent anything but Windows from installing. 
This is not one of those, is it?
Nope, like I said before, I managed to install ubuntu on the very same laptop before.

---

### Post by oldfred on 2014-12-02
My motherboard that shows similar USB- options for booting, only booted from a hard drive entry in BIOS. 

And flash drive had to be bootable when I rebooted to boot from hard drive entries. So make sure you have installed ISO to flash drive, not copied it and that ISO you downed is good.

 Note issues with 14.10 and older versions.
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801)
And these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

