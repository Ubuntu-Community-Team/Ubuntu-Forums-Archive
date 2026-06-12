---
title: "installing a canon mp980"
date: 2022-05-07
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-05-07
I am trying to install a canon mp980 onto my computer as a wireless printer.  I have, I think, done the wireless thing but when the printer is found, and connected, it is no longer the pm980 but, rather, CUPS_BRF_Printer.  I have also installed printer-driver-gutenprint (5.3.3-4) onto my machine but can't figure out how to deal with the CUPS_BRF_Printer and the gutenprint driver.  I am missing something but can't figure it out.

Thank you.............

---

### Post by jgw on 2022-05-10
I have attached a photo of my printers in 'settings'.  I now have two cups printers which should only be one (canon mp980), the first one which also has the gutenburg driver.  It also is showing two Dymo Labelprinters.  There is only one of those too.  I have tried to remove the two wrong printers but I dismiss them and they appear again!

the Dymo printer is plugged into the computer and works fine.  The ms980 is, in theory connected by wifi.  I have tried to print with it.  The computer says its sending to the printer and then says its all printed.  There is nothing printed.  

Anyway, how do I get rid of the printers that are not there?  
How do I make the printer actually print?

I have tried to do both of the above and failed.

Thoughts?

---

### Post by #&amp;thj^% on 2022-05-10
To add or remove a printer, open browser and paste:
```
http://localhost:631/ 
```
you will need Admin rights.
Also just in case you need more: [https://www.cups.org/doc/network.html](https://www.cups.org/doc/network.html)

---

