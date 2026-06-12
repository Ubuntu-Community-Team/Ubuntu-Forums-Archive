---
title: "Server install Failing"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by robertsaron on 2009-12-26
After multiple install attempts failing for server install, and burning 3 DVDs 2 different ways. The server for 9.10 32bit says it is installed, then goes to reboot. Message that comes up after it ejects the DVD to boot to hard drive is: NO DISK OR BOOT FAILURE PLEASE INSERT SYSTEM DISK.

I have installed it MULTIPLE TIMES, and after dozens of reboots, that message always comes up.

the processor is AMD athlon xp 64bit, 3 gigs of ram, 2 hard disks SATA drives: 1 disk is 100gigs, other disk is 250gigs. Attempted to install to both disks, and failed on each one. Even put in an ubuntu live cd, WIPED ALL partitions on both disks, and still same message. Motherboard is MSI K8nNeo4Platinum. The CD/DVD drive is a Pioneer Dual layer burner, sata as well.

Ubuntu server seems to be a POS. I only wanted to set up a smb server and a KVM box for virtual machines. The boot priority in the BIOS from first to last is CD ROM drive, USB FDD, hard disk.

any ideas? suggestions? going to change the drives order around and then post update. if that does not work, time to try a different Linux flavor for server.

---

### Post by blackened on 2009-12-26
I would lean towards bad media. Start by burning the disc at the slowest speed possible. If that doesn't help, then try a different brand of media. I know it sounds silly, but I have good luck with only a few brands and the rest are coaster city (ahem Memorex).

---

### Post by robertsaron on 2009-12-28
Bad media is possible, have had that happen before. I do not have any other, unless room mate will let me have a cd. Though 3 DVDs in a row that are bad is highly unusual. 

Dropping the burn speed is a good idea. The media I am using is TDK.

---

### Post by blackened on 2009-12-28
TDK usually makes good media. Drop the speed and see what happens. 1x and 2x are slow as molasses, but slow and good is better than fast and nonfunctional.

---

### Post by robertsaron on 2009-12-31
Burned at slower speeds, i do not think the server install liked DVD media. Never been a problem before. So going to try using a USB thumb drive to install it.

Hope it works if not then time to buy some CDs.

---

### Post by blackened on 2009-12-31
I always keep a store of CDs around for that very reason.

The USB startup disk creator available under System -> Administration is invaluable if you plan on going the USB install route.

---

### Post by robertsaron on 2010-01-01
Grub was not being written to the MBR. And the menu.lst was not being created. I had two hard drives 100gig connected to my motherboards sata1 connection, 2nd drive is 250gigs connected to mother boards sata5 connection. My mother board has 8 sata connections. the 250 gig drive had the OS and the MBR did not get written to the first drive. It was being written to the second one. 

I pulled out the primary drive, 100gig, and then moved the second drive, 250gig from sata5 to sata1. OS loaded just fine then.

Which is odd because at one point i wiped the partitions on all drives and installed the OS onto the 100gig drive. So it should have worked unless the drive has gone bad.

---

