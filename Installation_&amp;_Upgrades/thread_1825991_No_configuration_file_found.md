---
title: "No configuration file found"
date: 2011-08-16
forum: Installation &amp; Upgrades
---

### Post by Jigar L on 2011-08-16
I made a bootable USB flash drive for ubuntu 11.04 32bit. 
I went to the setup and setup the booting option to USB drive. Now I am trying to boot from USB drive it give an error message: 

SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1994-2011 H. Peter Anvin et al
ERROR:  No configuration file found
No DEFAULT or UI counfiguration directive found!
boot: _

Can someone please help me?

---

### Post by varunendra on 2011-08-16
Hi, and welcome to the forums!

How did you create the Live USB? Either use the inbuilt USB Startup Disk Creator program from the live environment, or use [unetbootin]("http://unetbootin.sourceforge.net/").

Also, make sure the downloaded iso file is intact (create md5checksum with this tool: [http://www.softpedia.com/get/System/File-Management/MD5-Check.shtml](http://www.softpedia.com/get/System/File-Management/MD5-Check.shtml)
and compare it with the original one given here: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes))

---

### Post by PaeTar on 2011-08-19
I found formatting into just FAT not 32 and using unetbootin and allowing it to download it's own version allowed me LIVE boot. Every .iso I downloaded on my own didn't seem to let me boot in.

---

### Post by woolfie on 2011-12-08
Similar to PaeTar, I found for my older laptop it wouldn't work if the USB was formatted with a FAT32 partition, but once I formatted as FAT16 things are going a lot better. Perhaps that should be an option in the startup disk creator?

(Btw, technical info and other possible remedies at the syslinux page [https://wiki.archlinux.org/index.php/Syslinux#Manual_Install_-_syslinux](https://wiki.archlinux.org/index.php/Syslinux#Manual_Install_-_syslinux))

---

### Post by roopeshmicasa on 2012-07-07
The root cause to this system error is FAT32. 
I think your Bios cannot understand FAT32 file system. May be your  system is old one. Format the USB with FAT16, or simply FAT file system  and then create the usb bootable stick that will definitely work....

---

