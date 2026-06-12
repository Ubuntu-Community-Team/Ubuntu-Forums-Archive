---
title: "MacBook won´t install Ubuntu..."
date: 2015-03-02
forum: Installation &amp; Upgrades
---

### Post by benjamin35 on 2015-03-02
Hi to all, i´m new here...

I´m trying to get Ubuntu running alongside Mac OS (10.6.8) and it´s not working.

I´ve used different ways of creating a LiveUSB or a DVD from the 14.4.02 iso (with Disk Utility, with unetbootin, 
via the terminal ([http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx))).

The problem is that if i use the DVD for the boot all i see on my screen is: 

"1.

2.

Select CD-ROM Boot Type: _"

and i can´t do anything....

If i use the LiveUSB i get:

"Starting legacy loader
Using load options ´USB`
Error: Not Found returned from legacy loader
10x Error: Not Found from LocateDevicePath
Error: Load Error while (re)opening our Installation volume"

And then the message: "The firmware refused to boot from the selected volume. 
Note that external hard drives are not well supported by Apple´s firmware for
legacy OS booting."

I have a 2006 Macbook 2,1. Core 2 duo, 2x1GB RAM, Crucial MX 100 SSD (256GB)

If anyone has an idea how to solve this it would be greatly appreciated.

Thx, benjamin

---

### Post by DarkSapphire on 2015-03-19
1. Did you check the md5 sum?  Here is the link the hashes [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and how to check md5 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM).   You will be able to just use your terminal

2.  Try a different USB, some USBs have bloatware on them that messes up installation 

3.  Since your on a Mac, go into disk utility, and make sure your usb is formatted in MS-DOS FAT

After doing all of that, do it again. You would be surprised that doing it another time would work.

---

