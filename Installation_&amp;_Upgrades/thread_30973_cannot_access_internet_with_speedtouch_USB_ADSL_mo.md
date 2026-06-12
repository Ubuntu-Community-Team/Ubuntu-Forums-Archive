---
title: "cannot access internet with speedtouch USB ADSL modem"
date: 2005-05-01
forum: Installation &amp; Upgrades
---

### Post by oldcodger on 2005-05-01
I have installed Kubuntu superficially satisfactorily, and am now trying to follow 'The Linux Kernel Speedtouch  Driver for Ubuntu Hoary Hedgehog' to access the internet. 

The system has recognised my SpeedTouch 330 modem and given me vendor, prod ID, Rev, manufacturer, etc, and I have downloaded the various files needed for the installation, and copied these onto a floppy. But when I try to follow the instruction to copy these into my home folder and make sure that firmware-extractor is executable (cp -r /media/floppy/* . && chmod +x firmware-extractor), I get the response:
'cannot stat /media/floppy has not been recognised'.
 :( 
Help!

old codger

---

### Post by oniko0 on 2005-05-02
The same happens to my SpeedStream 4060 USB modem. 

After a call to my ISP, the response was that "Linux does not currently allow USB modems to connect to the internet", or something along those lines.

The solution is to get an ethernet connection. I believe we need to buy ethernet modems or else buy an ethernet network card. 

Cheers.

Oniko

---

### Post by oldcodger on 2005-05-03
[QUOTE=oniko0]The same happens to my SpeedStream 4060 USB modem. 

After a call to my ISP, the response was that "Linux does not currently allow USB modems to connect to the internet", or something along those lines.

/QUOTE]

This is odd. I don't know about Speedstream 4060 but, in addition to posting on this forum, I also posted on the SpeedTouch Mailing List [[http://www.mail-archive.com/speedtouch@ml.free.fr]](http://www.mail-archive.com/speedtouch@ml.free.fr]) where I'm in discussion re the procedure given in the guide: 'The Linux Kernel SpeedTouch Driver for Ubuntu Hoary Hedgehog' [[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html]](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html])

HTH. Best
oldcodger

---

