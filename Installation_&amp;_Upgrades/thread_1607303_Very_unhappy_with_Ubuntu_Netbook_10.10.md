---
title: "Very unhappy with Ubuntu Netbook 10.10"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by speedygeo on 2010-10-27
Unity is a wonderful desktop at the first look.
But I can't install it on my netbook.
I tried to create a usb stick with unetbootin from PartedMagic 5.6 and Sabayon but the install process crash near the end. Testing the disk I obtain the result that there is a file error. I tried to download again, but I have the same error.
I create the startup usb stick with the Ubuntu utility, but at boot time it say "Unknown keyword in configuration file".
I have a Fujitsu-Siemens Amilo Mini Ui 3520.:confused::mad:

---

### Post by sikander3786 on 2010-10-27
Why don't you try with some other USB stick or with a CD if possible.

The error sounds like your USB disc in unreadable at some point.

---

### Post by movieman on 2010-10-27
Try:

[http://ubuntuforums.org/showthread.php?t=1183783&page=2](http://ubuntuforums.org/showthread.php?t=1183783&page=2)
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

---

### Post by speedygeo on 2010-10-28
I have the ubuntu desktop iso that works. I installed on the stick that iso and works. After that I installed ubuntu-netbook package, and now I have Unity.
Thanks for suggestions.
I never burned a CD for netbook edition. If you do that, please test the CD integrity at grub time see If 10.10 image iso have problems I reported.
For me the problem is solved, but I think the iso have the problem unsolved.

---

### Post by rinaldow on 2010-10-28
> **speedygeo said:**
> I have the ubuntu desktop iso that works. I installed on the stick that iso and works. After that I installed ubuntu-netbook package, and now I have Unity.
Thanks for suggestions.
I never burned a CD for netbook edition. If you do that, please test the CD integrity at grub time see If 10.10 image iso have problems I reported.
For me the problem is solved, but I think the iso have the problem unsolved.

maybe, just maybe the usb drive is wrongly formatted?
try fat16, otherwise didnt work out for me on my netbook when trying to install ubuntu...
the same for upgrading the bios...

Good Luck :)

---

### Post by speedygeo on 2010-10-28
When I used Unetbootin I formated FAT16, but after when I used the ubuntu utility that utility erased and formatted the stick without ask me.

---

### Post by rinaldow on 2010-10-29
Maybe you should use UltraIso, its used in windows-environment, but very useful.

if you got a friend with vista or win7 system you can install a trial version of UltraIso, it works.

Steps to do:
-copy iso image to window$computer
-format usb-drive to FAT16
-start UltraIso (With Administrator rights) and open file (CTRL+O), locate the iso and double click it.
-go to "Bootable" menu and click on "Write Disk Image"
-make sure the correct disk drive is chose, in this case your usb-drive
-choose the "USB-HDD+" option and click on "Write".

restart you netbook with usb when UltraIso is done writing, and you should be good to go...

If the problem still persists, I'd like to know...
Good Luck!

---

