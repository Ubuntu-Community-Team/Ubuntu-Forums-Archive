---
title: "Why do I got the error trying to install Ubuntu from USB ?"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by violeta2 on 2016-11-11
I got the mistake when I tried to install Ubuntu from USB to my computer. It sounds:
"Recovery. Your PC/Device needs to be repaired. The boot configuration data file is missing some required information. File:\BCD Error code: 0xc000000d You'll need to use recovery tools. If you don't have any installation media (like a disc or USB device), contact your PC administrator or PC/device manufacturer." 
What I should do that to repair this mistake ?

---

### Post by bearlake on 2016-11-11
What version of Ubuntu?

Where did you download the ISO file from?

Did you check the md5sum against the file downloaded?

---

### Post by coffeecat on 2016-11-11
> **violeta2 said:**
> File:\BCD Error code: 0xc000000d You'll need to use recovery tools. If you don't have any installation media (like a disc or USB device), contact your PC administrator or PC/device manufacturer.

Googling suggests this is a Windows error message.

In order for members to help you, please provide more details. Apart from what bearlake asked you, details of your hardware, what version of Windows you have, how far did you get with trying to install Ubuntu?

---

### Post by violeta2 on 2016-11-12
I have Ubuntu 16.04.1. I took the ISO file from ubuntu.com to my USB. I don't know what it is [COLOR=#000000]md5sum. I tried to install Ubuntu to the new laptop Lenovo which has not any operating system. My file looks like this: ubuntu-16.04.1-desktop-amd64 and I am able to attach the photo of this because I don't understand how to add URL here. [/COLOR]

> **coffeecat said:**
> Googling suggests this is a Windows error message.

In order for members to help you, please provide more details. Apart from what bearlake asked you, details of your hardware, what version of Windows you have, how far did you get with trying to install Ubuntu?
I googled but I don't understand the video because there are the different OS maybe. I have Windows 7 Ultimate on my laptop and I don't have any operating system on another laptop. I need to install Ubuntu 16.04.1 from USB to my empty laptop but when I tried to do it then I got the recovery message. I maybe pushed F7 or F8 too long during the trying to install Ubuntu to the empty laptop Lenovo.
By the way, where is the 'volume-down' button ?

---

### Post by oldfred on 2016-11-12
From Ubuntu live installer in live mode, run this:
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by yancek on 2016-11-12
The message in your original post is a windows error and has nothing to do with booting Ubuntu or any Linux.
Possible problems are that you haven't set the BIOS to boot from the flash drive, you have a bad download of the iso or it wasn't copied to the usb correctly.  What software did you use to put Ubuntu on the usb drive you are using?

---

### Post by violeta2 on 2016-11-12
That to put Ubuntu on the USB drive I used Windows 7 Ultimate.

---

### Post by Johnathan_Simpson on 2016-11-12
I know its not a ubuntu issue but you need to get a widows usb/cd and use [this]("https://neosmart.net/wiki/your-pc-needs-to-be-repaired/#Cause_1_BCD_ismissing_or_corrupt") guide Fix #4. That is what i used to fix same bcd error after deleting wrong entry with easyUEFI.

---

### Post by violeta2 on 2016-11-12
> **oldfred said:**
> From Ubuntu live installer in live mode, run this:
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
If I understand correctly that the "Boot Repair" is in Ubuntu ? I don't have Ubuntu. I have only Windows 7 Ultimate.

---

### Post by oldfred on 2016-11-12
I thought you had installed Ubuntu's ISO onto a flash drive.
Or did you just copy it?
ISO is a compressed image and must be extracted, flash drive reformatted, files copies into flash drive and flash drive made bootable.
The Windows tools to install ISO to flash drives do all that automatically.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[URL="http://www.ubuntu.com/download/desktop"]http://www.ubuntu.com/download/desktop
[/URL]
 Windows 7 DVD video How to burn ISO to DVD  just over 1 minute
[http://www.youtube.com/watch?v=bAr6NkMvImA](http://www.youtube.com/watch?v=bAr6NkMvImA)
[http://windows.microsoft.com/en-us/windows7/burn-a-cd-or-dvd-from-an-iso-file](http://windows.microsoft.com/en-us/windows7/burn-a-cd-or-dvd-from-an-iso-file) 

      
 Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)
You can use Win32 Disk Imager to install Ubuntu to a USB pendrive from Windows.
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    [URL="http://www.ubuntu.com/download/desktop"]
[/URL]

---

### Post by violeta2 on 2016-11-12
> **Johnathan_Simpson said:**
> I know its not a ubuntu issue but you need to get a widows usb/cd and use [this]("https://neosmart.net/wiki/your-pc-needs-to-be-repaired/#Cause_1_BCD_ismissing_or_corrupt") guide Fix #4. That is what i used to fix same bcd error after deleting wrong entry with easyUEFI.
What do you mean by "use [this]("https://neosmart.net/wiki/your-pc-needs-to-be-repaired/#Cause_1_BCD_ismissing_or_corrupt") guide Fix #4" ?

---

### Post by violeta2 on 2016-11-13
> **oldfred said:**
> I thought you had installed Ubuntu's ISO onto a flash drive.
Or did you just copy it?
ISO is a compressed image and must be extracted, flash drive reformatted, files copies into flash drive and flash drive made bootable.
The Windows tools to install ISO to flash drives do all that automatically.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[URL="http://www.ubuntu.com/download/desktop"]http://www.ubuntu.com/download/desktop
[/URL]
 Windows 7 DVD video How to burn ISO to DVD  just over 1 minute
[http://www.youtube.com/watch?v=bAr6NkMvImA](http://www.youtube.com/watch?v=bAr6NkMvImA)
[http://windows.microsoft.com/en-us/windows7/burn-a-cd-or-dvd-from-an-iso-file](http://windows.microsoft.com/en-us/windows7/burn-a-cd-or-dvd-from-an-iso-file) 

      
 Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)
You can use Win32 Disk Imager to install Ubuntu to a USB pendrive from Windows.
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    [URL="http://www.ubuntu.com/download/desktop"]
[/URL]
I downloaded the ISO file from ubuntu.com to my Windows 7 Ultimate. Then I copied (or maybe installed ?) the ISO file to my USB flash device. But when I open "Windows Disc Image Burner" of my ISO file on Windows 7 then the option "Disc Burner:" is empty. I got the message below "A disc burner wasn't found. Make sure that a burner is installed properly and you have the appropriate permissions to burn a disc."

---

### Post by oldfred on 2016-11-13
You cannot copy ISO to flash drive, it still needs to be on hard drive for installer software to be  able to install to flash drive.
If one option to convert ISO to flash drive is not available, try one of the others.

---

### Post by violeta2 on 2016-11-13
> **oldfred said:**
> I thought you had installed Ubuntu's ISO onto a flash drive.
Or did you just copy it?
ISO is a compressed image and must be extracted, flash drive reformatted, files copies into flash drive and flash drive made bootable.
The Windows tools to install ISO to flash drives do all that automatically.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[URL="http://www.ubuntu.com/download/desktop"]http://www.ubuntu.com/download/desktop
[/URL]
 Windows 7 DVD video How to burn ISO to DVD  just over 1 minute
[http://www.youtube.com/watch?v=bAr6NkMvImA](http://www.youtube.com/watch?v=bAr6NkMvImA)
[http://windows.microsoft.com/en-us/windows7/burn-a-cd-or-dvd-from-an-iso-file](http://windows.microsoft.com/en-us/windows7/burn-a-cd-or-dvd-from-an-iso-file) 

      
 Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)
You can use Win32 Disk Imager to install Ubuntu to a USB pendrive from Windows.
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 
    [URL="http://www.ubuntu.com/download/desktop"]
[/URL]
I maybe copied or installed the  ISO file from my desktop to USB.But I have not [COLOR=#000000]extracted and not reformatted anything. I don't know how to do it. [/COLOR]

---

### Post by bearlake on 2016-11-13
> **violeta2 said:**
> I maybe copied or installed the  ISO file from my desktop to USB.But I have not [COLOR=#000000]extracted and not reformatted anything. I don't know how to do it. [/COLOR]

[This]("http://www.howtogeek.com/howto/9585/how-to-setup-a-usb-flash-drive-to-install-window") may help you.

---

### Post by Johnathan_Simpson on 2016-11-15
> **violeta2 said:**
> What do you mean by "use [this]("https://neosmart.net/wiki/your-pc-needs-to-be-repaired/#Cause_1_BCD_ismissing_or_corrupt") guide Fix #4" ?

"this" is a link to a few ways to fix the problem of bcd errors. The easiest is through the cmd of windows disc and selecting windows repair or something like that. On the windows 10 disc its on the bottom left. im sure its on the first menu of any of them. Just follow the steps and you should be back in business.

---

