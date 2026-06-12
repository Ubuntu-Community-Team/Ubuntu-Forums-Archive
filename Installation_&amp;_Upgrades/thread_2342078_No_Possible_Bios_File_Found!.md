---
title: "No Possible Bios File Found!"
date: 2016-11-03
forum: Installation &amp; Upgrades
---

### Post by zzzzak on 2016-11-03
Hi, im trying to boot my usb with xubuntu 16.04 but whenever i choose my usb from the boot menu appears a window like this one:  [IMG]http://files.jb51.net/file_images/article/201506/2015615112731880.jpg?2015515112739[/IMG]

I don't know why the bios think i'm trying to update it and i cant figure out how to make my usb boot properly.
Here it is my motherboard model :  Biostar G41-M7,  i'm using a SanDisk Cruizer Edge USb Flash Drive 8GB and unetbootin to burn the iso.

---

### Post by oldfred on 2016-11-04
Not familiar with your particular BIOS.
But most newer BIOS have three ways to update. Windows, DOS bootable flash drive, or from BIOS/UEFI but reading update file from flash drive.

So either you are directly booting into BIOS and it wants to find an update on flash drive. Or you still have DOS on flash drive and it is booting that, not the Ubuntu installer. That would suggest that installer was not created correctly.

We find (seeming random) cases where some brands of flash drives, some installers, and some USB ports do not work. Or just that combination of choices.
Some change installer & it works, some change flash drive and it works, and some just change which USB port and it works. Some have to redo everything.

First check that download of ISO is correct.
       [URL="https://help.ubuntu.com/community/HowToMD5SUM"]https://help.ubuntu.com/community/HowToMD5SUM

      [/URL]
 Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 
    [URL="https://help.ubuntu.com/community/HowToMD5SUM"]
[/URL]        
 these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by Geoffrey_Arndt on 2016-11-04
Suggest to use "Etcher" to transform/create the iso image into a usb bootable flash-stick:   [URL="https://etcher.io/"]https://etcher.io/

[/URL]

---

### Post by RobGoss on 2016-11-04
You can also try Rufus it seems to work great for most users [https://rufus.akeo.ie/](https://rufus.akeo.ie/)

---

