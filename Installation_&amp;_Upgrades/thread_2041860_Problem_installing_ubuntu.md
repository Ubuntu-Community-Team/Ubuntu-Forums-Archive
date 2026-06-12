---
title: "Problem installing ubuntu"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by Leeen on 2012-08-13
Hi, I'm very new in linux.
I'm trying to install ubuntu 12.04 in my laptop (Acer 5100 - 1GB - 2.0Ghz with Windows 7) 
I used unetbootin to set the image in a pen drive. When i boot from the pen drive, appears the unetbootin menu and i choose Install Ubuntu. It appears to start but suddenly stop and show me this:
busybox v1.18.5 (ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file system

Thanks for any help

---

### Post by robtygart on 2012-08-13
[IMG]http://sourceforge.net/apps/trac/unetbootin/raw-attachment/wiki/MiscWikiFiles/unetbootin-windows7.png[/IMG]

Did you download the ISO image or are you trying to download it using unetbootin? 

If you have the ISO images on your computer, did you click the "Disk Images" bubble?

Or you could Distribution and choose Ubuntu/Kubuntu/.... from the menu and it will download it from the web.

---

### Post by ajgreeny on 2012-08-13
The first thing to do is check the md5sum of the .iso image file you have against the listed values at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).

There are links there to show you how to do that from both windows and linux, if you are not sure.  If the value is not identical, you will need to download the iso file again, preferably using a torrent client, as that will check the hash sums as it downloads.

---

### Post by Leeen on 2012-08-13
I already had the image. I click the "Disk Images" bubble and search for the image. I tried with 12.04 and 11.04 and i have the same problem

---

### Post by Leeen on 2012-08-13
ajgreeny,
I've checked the md5sum and is exactly the same

---

### Post by intel on 2012-08-16
unetbootin is know to have problems 

luckily the debian/ubuntu linux isos are easy to simply dd
you need an image writer(Eg. Win32DiskImage.exe etc.)
 - OR - 
if  u have access to a linux machine simply use the 
dd command to write the iso to usb drive

cheers!

---

### Post by Leeen on 2012-08-16
I've tried with Win32DiskImage.exe and Linux Live USB creator and still have the same problem
The purple screen with the word Ubuntu appears and then the error

---

### Post by mastablasta on 2012-08-17
have you tried a different USB? perhaps it has errors.
 
you cna also try with a CD though it's not as fast.

---

