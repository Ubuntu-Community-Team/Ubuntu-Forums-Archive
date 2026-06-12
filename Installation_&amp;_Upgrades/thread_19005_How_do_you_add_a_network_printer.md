---
title: "How do you add a network printer?"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by zcox on 2005-03-09
Hi all - hopefully this is the correct forum to post in, if not please let me know a more appropriate one.

I have a HP PhotoSmart 2610 printer connected to my Linksys router (so it's not connected to another computer or print server).  I have several Windows machines successfully printing with it over the network.  The Ubuntu Add Printer wizard is great for local printers, but I'm having trouble setting up this network printer.

First off, I have no clue whether to use CUPS, Windows Printer, UNIX Printer, or HP JetDirect.  And then, I have no clue what parameters to use for each one.  Can anyone provide any sort of guidance?  [-o<

---

### Post by zcox on 2005-03-10
[QUOTE=zcox]Hi all - hopefully this is the correct forum to post in, if not please let me know a more appropriate one.

I have a HP PhotoSmart 2610 printer connected to my Linksys router (so it's not connected to another computer or print server).  I have several Windows machines successfully printing with it over the network.  The Ubuntu Add Printer wizard is great for local printers, but I'm having trouble setting up this network printer.

First off, I have no clue whether to use CUPS, Windows Printer, UNIX Printer, or HP JetDirect.  And then, I have no clue what parameters to use for each one.  Can anyone provide any sort of guidance?  [-o<[/QUOTE]
 I got it working using the "take a stab" approach. I looked at my router settings and got the IP address of the printer, then in the Add Printer wizard I selected HP JetDirect (not sure if this only works for HP printers?), put in the printer's IP address, left the default Port at 9100 and clicked next. My HP Photosmart 2610 wasn't in the printers list, so I downloaded the ppd file from linuxprinting.org and specified it. Then clicked apply and it worked!

---

