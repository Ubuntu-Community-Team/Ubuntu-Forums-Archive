---
title: "Ubuntu Desktop works OK, Installed server freezes after &quot;booting the kernel.&quot;"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by ekh on 2006-07-17
Hi

I am new to Ubuntu. As I am trying to get the understanding of the "Enhanced Machine Controller, "EMC2" (running on Ubuntu), I caught interest in using the Ubuntu LAMP server.

I have browsed the first 3 pages in this forum, others have similar problems, but I don't progress so far in the boot sequence.

The PC:
VIA Technologies EPIA-M motherboard 1GHz with 512MByte RAM and 80GB Hitachi Deskstar IDE disk, IDE DVD burner and a floppy drive.
An extra ethenet port is added.

Currently this machine is running Mandrake PowerPack+ 10.0 dual firewall server.

I first changed the harddisk to another 80MB drive, and installed Ubuntu desktop 6.06. It seemed to work perfectly. I browsed the menus and tried a few things to get some feel of Ubuntu, no problems.

Then I erased the entire disk and installed Ubuntu LAMP server 6.06, the installation went without problems.

The install CD is burned at 4x speed.

When booting after the completed installation, the boot freezes, the last message on the screen is:

"Uncompressing Linux... Ok, booting the kernel." 

All messages on the screen stay put.

I have tried several things at the grub command line, all the files needed by grub seems to be there, But the machine is frozen.

Any help will be much appreciated.

ekh

---

### Post by tarvid on 2007-08-14
Use the "alternate" cd. Choose "text" (or command line). run tasksel and choose LAMP.

---

