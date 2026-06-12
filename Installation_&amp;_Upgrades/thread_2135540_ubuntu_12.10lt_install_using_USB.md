---
title: "ubuntu 12.10lt install using USB"
date: 2013-04-14
forum: Installation &amp; Upgrades
---

### Post by jetint8ke on 2013-04-14
i wnat to do a clean instal on my computer ,i go to the Cmos boot tab ,and the choices i have are:

C128
zip
atapi mo
usb fdd
usb zip 
 which one do i use to boot in ,so i can install ubuntu 12.10 Lt

---

### Post by jetint8ke on 2013-04-14
i did make my USB bootable using penguin

---

### Post by oldfred on 2013-04-14
If USB drive is bootable and plugged in, on my system it appears as another hard drive.

---

### Post by C.S.Cameron on 2013-04-14
You can create a Live USB using Startup Disk Creator from the Live CD or using UNetbootin.

---

### Post by jetint8ke on 2013-04-14
the only chioces are as follows
C128
zip
Atapi MO 
USB FDD
USB Zip

---

### Post by oldfred on 2013-04-14
Is your flash drive labeled c128? It may just show it by name.

---

### Post by jetint8ke on 2013-04-14
@ oldfred ,it's not c128,the only one that seems to boot up is USB FDD,but the screen is black and there is a cursor the runs from right to left ,thats it ,i let the computer furn for 30 minutes to see if it was installing very slow and nothing happen ,the computer i want to install it on ,has no operating system on it,oh and i did try doing it with unetbooting also and nothing happen

---

### Post by oldfred on 2013-04-14
If you use ATAPI what does that give? That should be a hard drive.

FDD refers to a floppy drive, so it was having trouble reading your floppy drive connected by USB. It may have tried reading the flash as a floppy but the data is formatted so differently it would not ever work.

---

### Post by jetint8ke on 2013-04-14
@oldfred,i tried all the choices avialible the only one that pretends to work is USBFDD,and i only get acursor running at the bottom of the black screen

---

### Post by oldfred on 2013-04-14
Are you sure USB flash drive is correctly configured. With my systems they do not show in BIOS unless bootable.

---

### Post by jetint8ke on 2013-04-17
i finally got the other computer to boot from the USB ,now the problem is that the monitor goes black and says ,no signal ,and it shuts off

---

### Post by oldfred on 2013-04-17
What Video do you have?
I had similar with my nVidia, but when installing from flash drive I noticed install was proceeding, just monitor was off.
Since they change something in kernel many version ago I have had to use nomodeset on every live boot or first boot after install or until I install nVidia drives from repository.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


 Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

