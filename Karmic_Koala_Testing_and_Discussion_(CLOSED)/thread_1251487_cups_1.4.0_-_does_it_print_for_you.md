---
title: "cups 1.4.0 - does it print for you?"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-08-27
After recent update of CUPS printing jobs just stall in "processing..." forever. Is it for you also?

---

### Post by alphacrucis2 on 2009-08-27
> **ilna said:**
> After recent update of CUPS printing jobs just stall in "processing..." forever. Is it for you also?

It's working ok for me with an ip connected printer. I notice though that trying to select the printer properties from the menu does nothing.

---

### Post by ayates on 2009-08-27
I just added a "me too" to your bug report.
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420216](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420216)

---

### Post by ilna on 2009-08-27
> **ayates said:**
> I just added a "me too" to your bug report.
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420216](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420216)Thanks! - You have added it faster rather I supplied a ref to the bug here :-)

---

### Post by garvinrick4 on 2009-08-30
Here is a fix for you if you still have problem. If it is a USB printer.

terminal Type: lsusb   (will see dev #'s and bus #'s for computer)

sudo rmmod usblp    
sudo aa-complain cupsd
sudo chgrp lp/dev/bus/usb/3 digit bus #/3 digit device #
sudo chmod 664 /dev/bus/usb/3digit bus#/3 digit device #

Go to graphic interface to add printer manually   System>Administration>Printing> Click New
                                                                                                                or CTRL +N
System will then find USB device and driver if necassary.


Linux instructions  Ubuntu 9.10 Karmic Koala Alpha 4   (intent to make CUPS see USB Printer)
                                                                                        and driver

---

### Post by garvinrick4 on 2009-08-30
Third sudo command space after lp

---

### Post by Moop on 2009-08-30
Same here on my networked HP Laser Jet 1020.

---

### Post by gwenn on 2009-08-30
Same for me . My system sees the printer -an Epson C80 - but is still processing...

---

### Post by ilna on 2009-08-30
> **ilna said:**
> After recent update of CUPS printing jobs just stall in "processing..." forever. Is it for you also?

To summarize:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015)
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420797](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420797)
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/421459](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/421459)

---

### Post by arvevans on 2009-08-30
arv@arv-desktop:~$ lsusb
Bus 001 Device 003: ID 04b8:0838 Seiko Epson Corp. CX7300/CX7400/DX7400
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c03d Logitech, Inc. M-BT69a Pilot Optical Mouse
Bus 003 Device 003: ID 0ac8:3330 Z-Star Microelectronics Corp. 
Bus 003 Device 002: ID 0451:1446 Texas Instruments, Inc. TUSB2040/2070 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
arv@arv-desktop:~$ sudo rmmod usblp
[sudo] password for arv: 
ERROR: Module usblp is in use
arv@arv-desktop:~$ sudo rmmod usblp
ERROR: Module usblp is in use
arv@arv-desktop:~$ 


OK...what next?

---

### Post by ilna on 2009-08-30
Add the module to  /etc/modprobe.d/blacklist.conf and reboot. As far as I understand there isn't another absolutely correct way to rmmod a module at case last one is in use.

---

### Post by gwenn on 2009-08-30
g:~$ sudo rmmod usblp
ERROR: Module usblp does not exist in /proc/modules

---

### Post by ilna on 2009-08-30
As far as the module isn't loaded you can forget it at all :-) and continue with other steps.

---

### Post by maestrobwh1 on 2009-08-30
No and my printer has worked since Ubuntu 6.10!

Cups via browser does not even find the printer.  Again, it was ALWAYS listed.

If I use package "printconf" (python) then it finds it in the terminal and then it shows up as 

pagepro_1350w	KONICA MINOLTA PP1350W	USB Printer #1	Minolta PagePro 1350W Foomatic/min12xxw (recommended)

Description:	KONICA MINOLTA PP1350W
Location:	USB Printer #1
Driver:	Minolta PagePro 1350W Foomatic/min12xxw (recommended) (grayscale)
Connection:	usb:/dev/usb/lp0
Defaults:	job-sheets=none, none media=na_letter_8.5x11in 

However, it does not print.  It works in jaunty, knoppix 6.01, arch linux with the same driver min12xxw

---

