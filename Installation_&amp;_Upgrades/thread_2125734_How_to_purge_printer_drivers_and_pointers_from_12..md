---
title: "How to purge printer drivers and pointers from 12.04.2"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by alvinmoneypit on 2013-03-14
Printer didn't work after installing 12.04.2 yesterday.  System saw my usb printer, offered driver but would not download it (internal server error external server error" was the code on the GUI).  I tried to get it working with[ this HowTo]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters#Lexmark%20Z600%20Series%20Printers").  I thought I did everything correctly, but terminal gave "warning! alien not running as root!" but it looked like everything loaded in the proper places, except ping did not work in step 9.  After going through the HowTo, now it doesn't see the printer at all anymore.  
So I was hoping someone could explain how to purge all printer drivers and pointers from terminal or any other method so I can get back to where I was as the system was at least seeing the correct printer, just wouldn't load the driver for some reason.  Thanks for all replies.

---

### Post by alvinmoneypit on 2013-03-18
I got it working by using [this HowTo]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters") to locate the [Z600 driver]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb") and the i386 libstdc++5 I got from Synaptic. First got libstdc++5, then downloaded the Z600 driver. Get the ppd file out of the driver package by simply clicking on the package and extracting the ppd with Archive Manager.
    Then I installed with the onboard printer installer- 1) select printer, click forward; 2) program searches for driver, click 'cancel' if it finds one, click "forward"; 3 "Choose Driver" screen comes up, click "Provide PPD file" navigate the browser lookup to where you extracted the PPD of Z600 and click forward. Then your printer is loaded and you can try to print. Hope this works for other seekers.

---

