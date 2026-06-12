---
title: "What is easiest/cheapest dialup modem for U804?"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by shultzjr on 2008-06-09
What is easiest (no compiling, moding, making or other bullsh*t) and cheapest (under $10) dialup pci modem there is for Ubuntu/Kubuntu 8.04?

thanks....

---

### Post by zoomzoomzoom on 2008-06-23
There are actually a few pci hardware modem cards out there, no new ones currently sold that I am aware of and they wouldnt meet your $10 limit if sold new.  However its possible if you are patient to snag used one on ebay.  The simplest way is go to ebay and do search for "pci modem linux", then screen them looking for ones that say hardware modem or onboard controller. 

 But if you want a real deal, do your homework, google pci hardware modem and start making a list of the various model numbers (most will be USR brand).  Especially keep eye out for those only offered as OEM modems.  Then do search on ebay for those model numbers.  Occasionally you will get some clueless individual selling one of these as a software modem.  There is your $5 shipped price pci card hardware modem.  And no I am not going to do your homework for you.  You want a cheap hardware modem, you earn it.  I remember I bought few of these over the years, one particular model that seemed easy to find but sorry cant remember the number anymore.

Now if you get over this have to have pci card modem, just buy an old external serial modem and if you dont have serial port, get a $5 serial to usb converter cable off ebay.  Look for the pl2303 (prolific) chipset cable, think they are bit better quality,  though any linux with kernel 2.6.24 or newer has the module built in to use a ch341 (winchiphead) chipset converter cable which are very common and very cheap on ebay.

---

