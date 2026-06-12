---
title: "Ubuntu can't find my HDD (hard disk) durning the installation of the system"
date: 2016-10-12
forum: MINT
---

### Post by marcop2 on 2016-10-12
Hey All, Im literally going crazy...
Im trying to install Ubuntu (and then Mint) on my desktop pc, as unique operative system, easy right? Nope!
When the boot of the os start (im installing via usb) everything goes ok until i have to chose where i want to install Ubuntu.
The o.s. try to install his-self inside the usb key without allow me to select where.
I've follow some guides finded here, and i have discovered that ubuntu did not recognize my hdd.

I try to use Gparted, and this is the output:

[IMG]https://s9.postimg.org/syjocsldb/14699529_276776436055245_977093506_o.jpg[/IMG]

my pc mount:  

CPU: AMD Athlon(tm) x4 750k Quad Core Processor
Graphic Video: GeForce GTX 650
HDD: ST2000DM 001-1CH164 SATA Disk Device

Priority device boot selected in the bios is sata.

Hope you can help me! And thank you!

---

### Post by QIII on 2016-10-12
Moved to MINT.

Forum Feedback & Help is for questions/issues with the operation of the forum software.

Cheers!

---

### Post by yancek on 2016-10-12
I notice the drive in your image is 'dev/sde' which would be the 5th drive in standard naming convention.  Have you clicked the down arrow to the right of /dev/sde in the upper  right to see other drives?  Is the primary drive empty?  You don't indicate it there is currently anything on it.  If you have some other OS installed and it is using the entire space it won't install.  Are you using the manual (Something Else) option rather than one of the auto-install methods?

---

