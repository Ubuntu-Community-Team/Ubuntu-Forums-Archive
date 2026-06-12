---
title: "Mobile Broadband"
date: 2012-03-29
forum: Installation &amp; Upgrades
---

### Post by Vsagar on 2012-03-29
[SIZE=4] First user of Ubuntu.Surprising versatility. But I have remove and reinsert my mmx 352G modem every time I open Ubuntu. 
           Can anybody help?
[/SIZE]

---

### Post by Mark Phelps on 2012-03-29
Found the link below -- but be warned, it's not a one-click solution:

[http://hashprompt.blogspot.com/2011/05/micromax-mmx-352g-usb-3g-modem-with.html]("http://hashprompt.blogspot.com/2011/05/micromax-mmx-352g-usb-3g-modem-with.html")

---

### Post by chandra2730 on 2012-09-23
Open terminal
type the following codes
"sudo gedit /etc/modules"

and then at the end of the line
type this

"usbserial
option"




and then restart your computer and connect the modem
then you'll see your modem
now create a new mobile broadband profile clicking on the edit connections and add new on mobile broadband tab
you must put RIGHT APN for your carrier


for
Indian carriers


TATA DOCOMO=tata.docomo.internet
AIRTEL=airtelgprs.com
AIRCEL=aircelweb
BSNL=bsnlnet
VODAFONE=www
VIRGIN MOBILE=vinternet.in





---------THIS WORKS FOR MY MICROMAX 352G MODEM WITH UBUNTU 12.04.

---

