---
title: "Presario B1200: Installation problems"
date: 2014-05-24
forum: Installation &amp; Upgrades
---

### Post by Eugene_Lee on 2014-05-24
I have a fairly old Compaq Presario B1200 which was overrun with malware and other unpleasant things, which nobody needed anymore. So I decided to use the disk sanitizer to wipe the hard drive, so that I could replace the old Vista OS with Ubuntu 14.04 LTS (32-bit)

I first tried using a live CD which appeared to work at first: 
1. Made sure that the disc drive was first in the boot order
2. I could reach the first menu where it asks me what I want to do with the Live CD (Try w/o installing, install directly, etc). I selected Install Ubuntu
3. Alt+Space --> Console appeared as expected, but then started throwing errors such as: end_request: I/O error, dev sr0, sector (some number) and SQUASHFS error: squashfs_read_data failed to read block (some number)
4. I left it overnight to just see if it would just do its thing, but unfortunately nothing much had changed, similar errors were appearing just like they were many hours before

Then, realising that the "dev sr0" meant something to do with the disc drive, I used Universal Usb Installer to install the same version of Ubuntu onto a formatted (FAT32) USB stick I had:
1. I went into the boot order again, but realised that there were multiple options with USB in the name: (in order)
Optical Disk Drive
USB CD-ROM
USB Floppy
USB SuperDisk
Notebook Hard Drive
USB Hard Disk
Network Controller
2. I removed the Live CD, put in the USB stick, and just hoped that since there was no other bootable media (wiped hard drive, Live CD taken out) that it would automatically recognise the USB stick
3. Computer displayed: Non-System disk or disk error, replace and strike any key when ready

I really do not know what else to do at this point...

---

### Post by ubfan1 on 2014-05-24
Just move all the USBs to before the hard disk.  The one you want is probably the USB Hard Disk, so I'd put that one first.

---

### Post by Eugene_Lee on 2014-05-25
Ok, I guess I'll try that. I'll see if it comes up with anything different.

---

### Post by Eugene_Lee on 2014-05-25
Aaaand guess what, it's working! thanks!

---

