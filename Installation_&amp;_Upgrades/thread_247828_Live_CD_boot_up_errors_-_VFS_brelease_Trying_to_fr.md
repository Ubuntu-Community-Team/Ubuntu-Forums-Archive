---
title: "Live CD boot up errors - VFS brelease: Trying to free free buffer"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by turbobill on 2006-08-31
I'm new to Linux, not computers.

At boot from CD on old Gateway Solo 2550 Laptop PC ...

VFS brelease: Trying to free free buffer
SQUASHFS error: sb_read failed reading block 0x71b2f
SQUASHFS error: Unable to read fregment cache block 1c6bc8e1
Unable to read page block 1c6bc8e1 size f60a
Buffer I/O Error on device hdc, logical block 234462
  the line above is repeated many times through block 234475
  where the machine hangs 

thanks for the help
Bill

---

### Post by oberwil on 2006-09-01
I'm getting something similar during install or Live CD with boot option acpi=off. I get this message during the Boot process. Most of the drivers, and configurations show OK before the machine hangs.

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

