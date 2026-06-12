---
title: "CUPS Stopping job because the scheduler could not open the output file"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by grandtoubab on 2009-09-26
Hello all,
My printer on usb is saw by cups but I can't print!
[RX425]("http://localhost:631/printers/RX425")RX425
Epson Stylus Photo RX425 - CUPS+Gutenprint v5.2.4Idle
in the log file this message "
E [26/Sep/2009:14:18:39 +0200] [Job 51] Stopping job because the scheduler could not open the output file."
What does it mean?
Thanks for any advice

---

### Post by grandtoubab on 2009-09-29
Hello all,
Below my status:
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04b8:080f Seiko Epson Corp. Stylus Photo RX425 scanner
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
I declare my printer as it:
sudo lpadmin -p RX425 -P /etc/cups/ppd/Stylus_Photo_RX420.ppd -v /dev/usbmon3
sudo chgrp lp /dev/bus/usb/003/002
sudo chmod 664 /dev/bus/usb/003/002
At this step no more errors in CUPS  error logfile but no output at the printer side!
Finally I created a new printer through CUPS [http://localhost:631/](http://localhost:631/) (seen as a RX420 despite it is a RX425???)
then deleted the old one (RX425)
Set the new one as partaged, enabled and default one
And all is working now!
I still do not understood why,  but it is ok for me as I am not an expert
 lpstat -t
le programmateur s’exécute
destination système par défaut : EPSON_Stylus_Photo_RX420
périphérique pour EPSON_Stylus_Photo_RX420 : usb://EPSON/Stylus%20Photo%20RX420?serial=LJ2030412222119500&i nterface=1
EPSON_Stylus_Photo_RX420 acceptant des requêtes depuis lun. 28 sept. 2009 18:21:33 CEST
l’imprimante EPSON_Stylus_Photo_RX420 est inactive, mais activée depuis lun. 28 sept. 2009 18:21:33 CEST
Finished page 1...

---

