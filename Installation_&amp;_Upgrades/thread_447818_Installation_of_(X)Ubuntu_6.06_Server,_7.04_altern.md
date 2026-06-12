---
title: "Installation of (X)Ubuntu 6.06 Server, 7.04 alternate hangs during install."
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by qwertzpoiu on 2007-05-18
Hello Folks

I have a problem installing (X)Ubuntu (same issue with Debian Netinstall) on an older computer which I'd like to use as a Fileserver.

I first tried to install  Debian which didn't work. So I tried using Ubuntu 6.06 Server Installation CD and after that (X)ubuntu 7.04 alternate install CD (burned 4x speed so the CD-ROM drive shouldn't have problems reading it).

The boot from CD works. The menu for chosing "install ubuntu on harddrive" ... "check CD for errors" .. etc. shows up. 

First try:
I chose "install on harddrive" and pressed ENTER. 
Two files (the latter one was initrd.gz or something) files were being unpacked or loaded (the dots filling the screen..) . 
After that the screen went black and there was only a horizontal line in the left upper corner  ( I suppose the cursor   ;-) ) blinking. 
The CDROM stopped spinning and AFAIK the SCSI Harddrive started spinning. 
I waited for some time (approx 5-10 minutes). Still nothing happened.


Second try:
I chose to exit the graphical menu by pressing ESC
on the commandline where it said "boot: " I wrote "install noapic nolapic pci=noacpi acpi=off" (found those options on forums where users had "similar" problems..) and pressed ENTER. Again .. it started loading those .gz files and then .. same thing .. screen went black and cursor was blinking.

Third try:
I chose "Check CDROM for errors".
After loading the .gz files the same blinking cursor showed up.


The specs of the computer:
- ASUS P2B Board: Bios Rev 1007
- Pentium 2 400Mhz
- 256 MB RAM
- ATI Rage 128 Graphics Adapter
- 2 x Promise Ultra 133 TX2 Bios 2.20.0.15 with 3 Hardisks connected
- Adaptec Array1000 Bios 4.20.23 SCSI Controller with one Harddisk connected
- some Floppy & CDROM
- In the BIOS plug&play OS is turned off. Shadowing of Memory is also turned off


If anyone could help me with this issue I'd be most thankful. Are there more boot options I should try out? 



PS: The computer ran FreeBSD before. So I think there must be a way to run some Linux Distribution on it, too.

---

### Post by qwertzpoiu on 2007-05-18
Ok ..  I don't why but somehow I got it working. Probably it was some temporary defect?

With the noacpi.. etc boot options I got the installation working.

Sorry for any inconvenience.

thread closed ...

---

