---
title: "trouble with usb startup disk creator and unetbootin"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by bth73 on 2010-03-10
running 9.10. upgraded from ultimate 2.0
usb creator only works with some iso's , anyone know why? Tried nimble X OS and won't work. I've tried many different ISO's , some work - most won't.

unetbootin says iso does not exist most of the time, (it will work off the built-in downloader), and when it does write a usb stick, the bootup fails sometimes w/ pup_420.sfs not found. dropping to initial-ramdisk console.

anyone know more than I do about this and can unetbootin do more than 4gig?

thanks

---

### Post by C.S.Cameron on 2010-03-10
I think usb-creator was designed to just make start-up disks from the Live CD it comes on.
I have not had too many problems with UNetbootin when installing items on it's list.
I could not get it to install NimbleX, It looked like it was starting to boot but would just count down and restart over and over.
Finally got NimbleX on a flash drive using the built in installer, the one that uses the existing FAT partition.
Other tools for making live USBs include BootMyIso and LinuxLive USB Creator.
I don't think UNetbootin has a 4GB limit unless you are talking persistence, but then it is a file size limit of FAT32. 
Persistence can be any size if you use a partition labeled casper-rw, and/or a partition labeled home-rw for a persistent home.

---

