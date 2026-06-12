---
title: "HDs not being recognised by BIOS after install"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by woolnough on 2010-05-16
Hi,

I've just installed 10.04 twice on 2 separate disks and it seems to have done something really strange to them.  BIOS will not recognise them anymore, it just waits but they never come online.  I have to unplug the disk completely for the system to boot.

The first time I thought I'd just lost a disk, but when exactly the same thing occurred the second time around, it seems like too much of a coincidence. 
 
The installer didn't recognise the disks first time around as they were part of a RAID group previously.  I did a 

[FONT="Courier New"]dmraid -E -r /dev/sda 
[/FONT]
to fix.  After that just installed as per every other time I've used.  

Any ideas? I'm baffled.


Matthew

---

### Post by woolnough on 2010-05-16
more info: 

BIOS gets to:

[FONT="Courier New"]Serial ATA AHCI BIOS iSrc 1.07 08042006
Copyright (c) 2003-2006 Intel Corporation
** This version supports only Hard Disk and CDROM Drives **
Please wait.  This will take a few seconds.


.............................
Controller Bus#00, Device#1F, Function#02: 06 Ports, 02 Devices
[/FONT]

If I change the disk to a different SATA connection, the system will go through the disks until it hits the one I installed Ubuntu on, then it just waits indefinitely. 

Matt

---

### Post by srs5694 on 2010-05-16
It could be you're running into a BIOS bug like the ones that can occasionally cause [GPT/BIOS incompatibilities.](http://www.rodsbooks.com/gdisk/bios.html) If so, and if you don't need the data that's currently on the disks, zeroing out the first 2MB (semi-randomly selected value) or so of the disks and creating fresh Master Boot Record (MBR) partition tables might fix the problem. If you want to keep your data, please provide more information: How are the disks partitioned? What filesystem(s) are you using? Are any partitions marked active/bootable?

---

### Post by woolnough on 2010-05-16
Excellent.  That link looks spot on.  I think I have my root cause.

Many thanks for that one.  

Now I've just got to find a PC that will boot with the Disk attached.

---

### Post by srs5694 on 2010-05-16
If they're SATA disks, you could try hot-plugging them. Alternatively, there are fairly inexpensive adapters to plug both PATA and SATA disks in via USB ports. You could use one of these and plug the disk in only after you've booted the computer.

---

