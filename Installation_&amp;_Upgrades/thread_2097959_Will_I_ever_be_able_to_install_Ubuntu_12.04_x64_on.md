---
title: "Will I ever be able to install Ubuntu 12.04 x64 on my machine??!!"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by trettet on 2012-12-25
I've been searching far and wide for solutions, answers, right procedur; used **Universal-USB-Installer-1.9.2.1 **and **UnetBootIn** but to no avail UBUNTU still FAILS TO INSTALL..
 
_System Specs:_
MSI P67-GD65 (B3)
Intel Core i7 2600k stock clock (3.40GhZ) HT-ON
EVGA Nvidia GTX 570 SC
PQI 4GB Value Ram (x2)
Thermaltake 900w PSU
WD 750GB Caviar Black Sata III
Windows 7 Home Premium 64 bit

_Flash Drive_
Kingston 2GB DataTraveler (Gen I or II??)
Tried both FAT and FAT32 FS's
 
_Ubuntu Version to Install/ISO Filename:_
***ubuntu-12.04.1-desktop-amd64***
**** 
**Error Shown:**
UnetBootIn w/ FAT - Boot Error
UnetBootIn w/ FAT32 - Boot Error

Universal-USB-Installer w/ FAT - no default or UI configuration directive found 
Universal-USB-Installer w/ FAT32 - no default or UI configuration directive found

[SIZE=1]**Note: 32 bit version of Ubuntu 11.x installed before on my system!!* [/SIZE]

---

### Post by carl4926 on 2012-12-25
You should use this if you only have a windows installation
[https://launchpad.net/win32-image-writer](https://launchpad.net/win32-image-writer)

---

### Post by fantab on 2012-12-25
How did you burn ubuntu.iso to USB? Have you burned it from Linux or Windows? 
Have you checked the integrity of you downloaded .iso with [**md5sum check**]("https://help.ubuntu.com/community/HowToMD5SUM")?
Do you have BIOS or UEFI/EFI?
What 'partition-table' do you have on your USB and HDD? 
Can you please tell us exactly and in detail what happens when you boot with LiveUSB?

On the face of it, to me, it looks like a corrupted USB filesystem or a bad burn. Try to format the USB file system to FAT32 using, preferably Windows. If you are using Windows I would suggest you try [**Win32DiskImager**]("http://sourceforge.net/projects/win32diskimager/") to burn you .iso to USB. (W32DI does not automatically detect .iso, after selecting the image you have to manually add .iso in the file selection dialog .)

---

### Post by trettet on 2012-12-25
> **fantab said:**
> How did you burn ubuntu.iso to USB? Have you burned it from Linux or Windows? 
Have you checked the integrity of you downloaded .iso with [**md5sum check**]("https://help.ubuntu.com/community/HowToMD5SUM")?
Do you have BIOS or UEFI/EFI?
What 'partition-table' do you have on your USB and HDD? 
Can you please tell us exactly and in detail what happens when you boot with LiveUSB?
 
On the face of it, to me, it looks like a corrupted USB filesystem or a bad burn. Try to format the USB file system to FAT32 using, preferably Windows. If you are using Windows I would suggest you try [**Win32DiskImager**]("http://sourceforge.net/projects/win32diskimager/") to burn you .iso to USB. (W32DI does not automatically detect .iso, after selecting the image you have to manually add .iso in the file selection dialog .)
 
Burned it to the usb using the softwares on my first post which were bold faced to indicate that they should be read :-| ...used Windows 7 SP1 w/ Latest Updates (Build 7601) it is written on my system spec that i got windows 7...ISO Integrity is okay for it matches the one on the documentation..MSI P67-GD65 uses UEFI...I don't know what's partition table.... my flash drive is brand new formatted it about 6 times with different Filesystems incl FAT and FAT32! because of this **_Ubuntu Installation madness_**... tried that Win32DiskImager but nothing WORKS!..flashes something that too fast that my eyes can't see, but i can see *_isolinux _*somewhere; it flashes than continues booting to windows 7...
 
EDIT:
> **fantab said:**
> Can you please tell us exactly and in detail what happens when you boot with LiveUSB?
 
that's what it outputs on the DOS-like thing on boot (y'know the gray text w/ black bg)

---

### Post by darkod on 2012-12-25
I would try unetbootin again. Format the stick as fat32 again. Start the unetbootin.exe with right-click, Run as Administrator (not with double click). It gives it more permissions in win7 to write the bootloader correctly.

While it's copying the content of the ISO, at the end watch out whether it will say the bootloader was done successfully too.

See if the same error pops up. If it does, it might be time to try another stick too, just to make sure it doesn't have anything to do with it.

---

### Post by trettet on 2012-12-25
oh forget it everyone.....ubuntu has caused too much problems for me...seriously!! (on version 11.x) i even accidentally wiped my whole hard drive..

I just tried to download and install ubuntu today because I saw a news that's about steam engine running better on ubuntu, steam going to be ported on ubuntu....
 
Even just installing **drivers** and **applications** IS **_VERY_** problamatic... i finally changed my view on this OS; this is just getting way to ridiculous... I've been having internet connection issues with Ubuntu 11.x and posted on this very forum...they told me to do that, and this and those and guess what nothing was solved...NOT TO MENTION the time I've wasted for waiting how many days i've waited for replies and time wasted to fix, reinstalling ubuntu and browsing other threads and posts for solutions..
 
Now i really don't care if you ban me or not on this forum (for ranting in the wrong place), because I will never be going back here again...seriously....it's way too [SIZE=3]**_troublesome_**[/SIZE]! ):P [SIZE=1][COLOR=dimgray]and time consuming[/COLOR][/SIZE]

---

### Post by darkod on 2012-12-25
Sorry, I don't know what issues you had before, but the issue you are talking about now has nothing to do with ubuntu.

The usb stick is not prepared correctly in windows. Burn a CD from the ISO and it will work right away. Or create the stick on ubuntu machine with Start Up Disk Creator and it will work.

Creating the ubuntu live usb on windows has nothing to do with ubuntu so don't blame it.

As for internet connectivity issues, usually wired internet works by default on most computers. Wi-Fi drivers can sometimes be an issue, but part of it depends on the manufacturer of the adapter having drivers to support linux. It's up to them.

---

