---
title: "HP Deskjet 1220C Installation woes"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by lasch on 2007-04-03
Originally when I tried to install the printer it was not detected. I could find the printer and suggested driver yet when I hit apply in step #3 the printer would not install. 

I ran the codes listed below as suggested and when I ran the printer wizard the printer was detected. I thought I was home free but the printer still would not install after hitting apply button.

Code:

lsmod | grep ppdev

if you don't see ppdev

run

Code:

sudo modprobe ppdev

and try configuring your printer again.

---

### Post by phidia on 2007-04-03
You might want to look at the linuxprinting.org page for that printer 
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_1220C](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_1220C)
maybe making sure you have the latest driver will help.

---

### Post by lasch on 2007-04-04
Thanks!! For whatever reason, downloading the driver from that site did the trick.

---

### Post by phidia on 2007-04-04
Cool! Thanks for letting us know what worked.

---

