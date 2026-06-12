---
title: "Karmic Not Detecting Printer"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Stabgotham on 2009-09-26
I just installed Karmic Koala (Ubuntu 9.10) and for some strange reason, it is not detecting my printer.  I have a Canon MP510 connected via USB.  Printer worked great in 9.04, but now Ubuntu won't even detect that I have a printer connected.  Any clues??

---

### Post by famous3warriors on 2009-09-26
Me Too I am having the same problem also. I have an Epson cx4600 and It shows that I can see it and everything but it does not print at all.:popcorn:

---

### Post by Stabgotham on 2009-09-27
This issue just doesn't strike me as being that hard to solve yet there has been no reply.  Is this a known issue with Karmic or something?

---

### Post by victor9098 on 2009-09-27
Similar problem here, but my USB ports do not even detect my USB key when I plug in.

---

### Post by john stiles on 2009-09-27
Sounds like the following bug:

[https://bugs.launchpad.net/ubuntu/karmic/+source/udev/+bug/420015](https://bugs.launchpad.net/ubuntu/karmic/+source/udev/+bug/420015)

In summary the following steps cure this for me:

Run

lsusb

and look for the line of your printer. The printer has a Bus and a Device number. Now run

sudo chgrp lp /dev/bus/usb/<bus number>/<device number>
sudo chmod 664 /dev/bus/usb/<bus number>/<device number>

with <bus number> and <device number> being padded with zeros to be always of 3 digits (8 -> 008, 11 -> 011, ...).

Example:

lsusb
Bus 002 Device 029: ID 03f0:1c02 Hewlett-Packard PhotoSmart A710 se
sudo chgrp lp /dev/bus/usb/002/029
sudo chmod 664 /dev/bus/usb/002/029

Then try to add a print queue and print to it.

---

### Post by grandtoubab on 2009-09-28
Hello all,
Same problem for me, unable to print !
Below my status:
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b8:080f Seiko Epson Corp. Stylus Photo RX425 scanner
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub I declare my printer as it:
sudo lpadmin -p RX425 -P /etc/cups/ppd/Stylus_Photo_RX420.ppd -v /dev/usbmon3
sudo chgrp lp /dev/bus/usb/003/002
sudo chmod 664 /dev/bus/usb/003/002


Lpstat give a good result (sorry it is in french)
lpstat -t
le programmateur s’exécute
destination système par défaut : RX425
périphérique pour RX425 : ///dev/usbmon3
RX425 acceptant des requêtes depuis lun. 28 sept. 2009 14:46:26 CEST
l’imprimante RX425 est inactive, mais activée depuis lun. 28 sept. 2009 14:46:26 CEST:P


 Now when I print it seems there is no error but nothing is printed ( when I use Jaunty Live Cd it is ok, the printer is working fine):confused::confused::confused:

---

### Post by grandtoubab on 2009-09-28
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b8:080f Seiko Epson Corp. Stylus Photo RX425 scanner
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Finally I created a new printer through CUPS [http://localhost:631/](http://localhost:631/) (seen as a RX420 despite it is a RX425???)
 then deleted the old one (RX425)
Set the new one as partaged, enabled and default one
And all is working now!
I still do not understodd why but it is ok for me

 lpstat -t
le programmateur s’exécute
destination système par défaut : EPSON_Stylus_Photo_RX420
périphérique pour EPSON_Stylus_Photo_RX420 : usb://EPSON/Stylus%20Photo%20RX420?serial=LJ2030412222119500&interface=1
EPSON_Stylus_Photo_RX420 acceptant des requêtes depuis lun. 28 sept. 2009 18:21:33 CEST
l’imprimante EPSON_Stylus_Photo_RX420 est inactive, mais activée depuis lun. 28 sept. 2009 18:21:33 CEST
    Finished page 1...
:guitar::P

---

### Post by Dilligaf on 2009-09-28
I have an Epson Stylus Photo r320 which has worked with Ubuntu for years, in Karmic it doesn't work. It's recognized as an MFP Composite Device 

Bus 001 Device 008: ID 04b8:011e Seiko Epson Corp. Perfection 1660 Photo
Bus 001 Device 007: ID 04b8:0812 Seiko Epson Corp. MFP Composite Device
Bus 001 Device 006: ID 0764:0501 Cyber Power System, Inc. CP1500 AVR UPS

The strange part is the included card reader works, the system just doesn't know it's a printer.

Mike

---

### Post by lemmy999 on 2009-10-07
@ grandtoubab

Thanks for the headsup re the CUPS workaround!

---

