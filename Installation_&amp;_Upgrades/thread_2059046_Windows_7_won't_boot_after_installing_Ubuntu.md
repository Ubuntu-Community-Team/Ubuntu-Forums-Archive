---
title: "Windows 7 won't boot after installing Ubuntu"
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by inohome on 2012-09-17
Hi all, 

I'm in emergency so I've to type it short and simple. Just now, I  downloaded the iso file of Ubuntu Alternate AMD64 and I extract it to  partition D (Windows is installed in partition C). After that, I reboot.  It went into the[[COLOR=blue][FONT=inherit !important][FONT=inherit !important] Ubuntu[/FONT][/FONT][/COLOR]]("http://www.tomshardware.com/forum/53262-63-emergency-windows-boot-installing-ubuntu#") setup without problem but when it start to format, it says CD source  not available or something like that because I didn't mention it that  time. Therefore, I reboot again but it takes me to the [[COLOR=blue][FONT=inherit !important][FONT=inherit !important]Ubuntu[/FONT][/FONT][/COLOR]]("http://www.tomshardware.com/forum/53262-63-emergency-windows-boot-installing-ubuntu#")  installation setup again, I reboot and I place the Windows 7 Home  Premium disc into my DVD drive and boot from it. I went in to delete the  partition D and never extended partition C and kept the unallocated  space, I reboot again. It says "Missing Operating System" and boot from  the Windows disc again, I click on[[COLOR=blue][FONT=inherit !important][FONT=inherit !important] Startup[/FONT][/FONT][/COLOR]]("http://www.tomshardware.com/forum/53262-63-emergency-windows-boot-installing-ubuntu#")  Repair and it took about 20 minutes and kept saying "Attempting  repairs...". Please help me, if you need any of my specs please reply,  thanks again. And yeah, some files are backup but some programs and big  sized videos are not and for the programs, I don't want to lose the  saved games and for the videos I don't want to download them again  because my internet speed is only 512Kilobits/s on here.

---

### Post by kaytrance on 2012-09-17
It seems that the installation messed up your master boot record. You can:

Repair it by step by step instructions [here]("http://support.microsoft.com/kb/927392"), but you won't see ubuntu boot option after.

Or you can try to reinstall ubuntu so that it tries to complete the installation and writes it's own data into MBR, so that you can dual-boot.

---

### Post by darkod on 2012-09-17
I don't understand how you tried to install from the ISO unpacked on partition D.

You should boot the computer with the ubuntu cd to install, not unpack it and try to run it from partition D.

Windows should be able to do the repair process but sometimes it needs to be run 3-4 times.

Or, you can boot with the ubuntu cd, and do the installation which will use the unallocated space you left by deleting partition D.

---

