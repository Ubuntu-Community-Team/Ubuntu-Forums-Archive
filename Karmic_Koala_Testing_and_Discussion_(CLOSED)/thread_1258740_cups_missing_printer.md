---
title: "cups missing printer"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pulpo69 on 2009-09-05
i have an usb-connected hp-printer. but ican't select it in system/administrati/printing because he don't show up.
in services cups is enabled. lsusb shows the printer.
the cupsd command gives the message Child exited on signal 15!
any idea?

---

### Post by taavikko on 2009-09-05
would help us, if we knew what printer it actually is
name, model and lsusb id

Did it use to work?

---

### Post by pulpo69 on 2009-09-05
output of lsusb:
Bus 006 Device 002: ID 03f0:2004 Hewlett-Packard DeskJet 640c

---

### Post by pulpo69 on 2009-09-05
and it worked

---

### Post by pulpo69 on 2009-09-06
nobody having the same problem?

---

### Post by lucazade on 2009-09-06
I've solved recreating cups config:

sudo mv /etc/cups/cupsd.conf.O /etc/cups/cupsd.conf
sudo service cups restart

---

### Post by pulpo69 on 2009-09-06
Thank you very much, this solved my printer problem!!

---

### Post by mattduckman on 2009-09-06
i had this same problem. I believe a bug should be reported that the configuration file provided with cups is empty.

---

### Post by pediatracancun on 2009-09-08
> **mattduckman said:**
> i had this same problem. I believe a bug should be reported that the configuration file provided with cups is empty.
This is already a known problem, you can find it in:
[https://bugs.launchpad.net/bugs/420015](https://bugs.launchpad.net/bugs/420015) 

Another solution is: 
#9   	 Till Kamppeter ( [https://bugs.launchpad.net/~till-kamppeter](https://bugs.launchpad.net/~till-kamppeter) )  wrote on 2009-08-28:  

As long as the AppArmor configuration for CUPS is not fixed yet, please run the command line

sudo aa-complain cupsd

and USB printing should work again.

As soon as a fixed CUPS package is there, return to the default mode via

sudo aa-enforce cupsd

---

