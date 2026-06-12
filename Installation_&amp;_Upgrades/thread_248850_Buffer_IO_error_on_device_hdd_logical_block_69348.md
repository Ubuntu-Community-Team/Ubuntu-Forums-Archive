---
title: "Buffer I/O error on device hdd logical block 69348"
date: 2006-09-01
forum: Installation &amp; Upgrades
---

### Post by oberwil on 2006-09-01
I'm getting an error during install or Live CD with boot option acpi=off. I get this message during the Boot process. Most of the drivers, and configurations show OK before the machine hangs.

I just burned a new CD and did a MD5CHECKSUM that was Good.

Here is the full specifications of my computer and error messages.

Computer: Asus A7V8X, AMD Athlon 2200+
Via KT400, Via VT8235
Promise PDC20376 chipset for SATA controller
Broadcom 4401 BCM4401 10/100 Ethernet
RealTek ALC650 audio 
IEEE1394 Firewire

Drives: Seatgate 120 gig Primary, WD 13 gig 2nd Master
Optical: Toshiba DVD-ROM SD-1502 Primary Slave
Optical: Plextor 1210/32 SCSI

Video: NVidea Geoforce 2 GTS 32mb PCI
Controller: Adaptec 2940AU SCSI.

Periferal:
Epson 1640u Perfection SCSI Scanner
HP Photosmart 1115 Pritner

Error Message with Live CD acpi=off:
266.806673 Buffer I/O error on device hdd logical block 69348
272.092445 VFS brelse Trying to free free buffer
272.094996 VFS brelse Trying to free free buffer
272.097431 VFS brelse Trying to free free buffer
272.099882 SQUASHFS error sb_bread failed reading block 0x21136
272.102617 Unable to read page, block 8447128 size 6a76

With install exactly same error message but the first digits are different. They start like
17179730.484000 Buffer " " "
35.900000 VFS brelse " "
35.904000 VFS " " "
35.904000 VFS " " "
35.908000 VFS " " "
35.912000 SQuASHFS " " "
35.912000 Unable to read " " "

If anyone could point me in the right direction, I'd appreciate it.

Thanks

Howard

---

### Post by Scunizi on 2006-09-01
You didn't mention if your harddrive is SATA.  If it is go to the download site for the ISO's and take a look at the release notes.  There's mention of how to turn off RAID after booting to the live cd and before attempting installation.  It took me 4 full install attempts before I figured out that one.  My errors were different by yours might be caused by the same issue.

---

### Post by oberwil on 2006-09-01
No, My Drives are not SATA.

Their both IDE. But maybe even though I don't 
have a SATA drive installed, maybe I have to
turn off support for it in the Bios.

I have a feeling it either is a bios setting, 
or it has to do with my motherboards chipset.

Howard

---

### Post by nadamsieee on 2006-10-23
Here are the instructions for turning off RAID arrays:

[http://www.ubuntu.com/download/releasenotes/606#head-f0fc50174e566788f02aa164fb6e80aa9c65ee24](http://www.ubuntu.com/download/releasenotes/606#head-f0fc50174e566788f02aa164fb6e80aa9c65ee24)

---

