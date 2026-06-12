---
title: "Semi-Freeze during install"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by bhd1223 on 2010-12-19
Hello all,
 
After many years I'm looking at jumping back into linux. I dabbled some about a decade ago but then became interested in other things and put this off. I'm back and am trying to install ubuntu-10.04.1-desktop-amd64.iso. I have this set up on a usb drive for intall using the universal usb installer. The platform I am trying to install on is an Asus UL80VT-A1 laptop.
 
The first problem I ran into required me to change the name of the folder isolinux to syslinux and then the files isolinux.bin and isolinux.cfg to syslinux.*** within that folder. After this I could actually boot from the usb drive and run ubuntu from the drive.
 
Everything appeared to be working. I had no video issues, both wired and wireless networking is functional, and everything I ran seemed smooth. The next and current problem was encountered during the attempted install. When trying to move forward from the keyboard layout step (3 of 7) the install appears to freeze and a crash report pops up. I can quit the install so it's not a full freeze but I've left it just sitting for over an hour and it remains on step 3. This was the 4th try and since the first, over 2 hours ago, I've been searching for a solution. It's happened when trying to install straight from the menu and also when installing while running ubuntu off the usb. I've come up dry and am looking for any input. I'd like to get this up and running asap.
 
Thanks in advance for any assistance.

---

### Post by sikander3786 on 2010-12-19
Welcome to the forums :-)

Try putting in some boot options by pressing F6 key as mentioned here.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

I think and hope that 'noapic' would work for you, but if it doesn't, there are 6 options and you need to try all of them one-by-one.

If that doesn't help, we need to know the hardware specs of your machine.

Also, check the downloaded image for defects.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If ok, try using some other utility for burning you image to the USB.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

I think you wouldn't need to rename the syslinux folders/files if created using Unetbootin.

Keep us posted :-)

---

### Post by bhd1223 on 2010-12-19
I tried the options first to no avail. It was a bit different then the link provided so maybe I missed something but what I tried didn't help. I then decided to try another trick I read about by formatting the drive as FAT rather than FAT32. Still no luck. I just finished using md5sum and the hash matches up properly. I'm about to attempt to use a different utility to burn the image to the usb. I wish I could find my blank cds...
 
Anyways to save some time I though I'd post up some specs.
 
Asus UL80VT-A1 Laptop:
Windows 7 Home Premium x64
Intel U7300 dual core CPU
4GB RAM
Switchable Mobile Intel 4 Series Express Chipset and NVIDIA GeForce G210M
Unknown HDD I believe was labeled as 320GB, assuming correct as just under 300GB is available on it.
 
Desktop:
Windows Vista Home Premium x64
AMD Athlon 64 x2 6000+ CPU
Asus M2N32-SLI Deluxe MOBO
8GB RAM - Some model of Corsair w/ purple on them
Hitachi Deskstart 700+GB HDD - may be 750GB HDD. Can't quite remember as it's been a few years since I built this system.
Main GPU - EVGA GeForce 9600 GT 512MB
Secondary GPU - unknown brand GeForce 6800 GS 256MB - used for second monitor
 
 
If anything else is needed please let me know. These are just the basic items that seemed easy to come up with.
 
I'm wondering if something regarding the HDD could be causing this issue. It appears the partition step is the one after the keyboard laybout during the install. On my drive I have 15GB unallocated space followed by 263GB for windows and then another 20GB unallocated. Would the unallocated space cause a problem when moving to the partition step? Do I need to format it somehow prior to this?
 
 
_Update_: Using the new utility for burning the image to the USB is still causing a halt when trying to move forward from step 3, keyboard layout. Would my guess about the HDD hold some validity or should I suspect this to be an issue elsewhere? I'm about to attempt the install on my desktop just to see what happens. That could help identify it as an issue with the laptop, correct?
 
_Update 2_: Same issue on my desktop. Freezing after clicking forward at the keyboard layout step (3 of 7). The drive is set up the same way with unallocated space. I think I'm going to give that a simple format and try again. The crash report icon told me it crashed on an assertion failure and this type of crash is not reportable. I'm assuming this is the same issue with the laptop.
 
_Update 3_: Still no progress from step 3. Formatting the unallocated space did nothing. The image appears to check out ok and it runs fine on my machines off the usb. I just can't seem to install it. I don't want to waste a dvd on the image but if anyone thinks that will solve the issue with the usb I'll give it a try.

---

### Post by bhd1223 on 2010-12-19
Solved:
 
Burnt image to a DVD using ImgBurn.  Stuck a few moments at step 3 but proceeded to partitioning.  Install successful.

---

