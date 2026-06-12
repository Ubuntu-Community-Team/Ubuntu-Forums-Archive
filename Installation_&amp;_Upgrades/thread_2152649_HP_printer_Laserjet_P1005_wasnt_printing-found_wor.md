---
title: "HP printer Laserjet P1005 wasnt printing-found workarounds"
date: 2013-06-08
forum: Installation &amp; Upgrades
---

### Post by rapattack1 on 2013-06-08
Ever since i got the latest Ubuntu Studio the printers and most usb periferals have been an issue. I have the HPLIP app installed but without first unplugging and replugging the usb cable in the back of the computer(not the printer) it will never work. OK then for a while now even that didnt make the system happy. So i went into HPLIP and re downloaded/installed the firmware. That works for one session only and i have to do it again when i want to print. Then today i tried something else. i Clicked on 'accepting jobs' in HPLIP and it allowed me to print. So these are some tips if your printer is not behaving. Hope this helps as this has been months and months and no answers anywhere on the net. I tried so many things though like reinstalling plus step by step guides i saw....nothing worked.[ATTACH=CONFIG]243659[/ATTACH]

---

### Post by rapattack1 on 2013-06-15
> $ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:08c9 Logitech, Inc. QuickCam Ultra Vision
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 003: ID 04f3:0230 Elan Microelectronics Corp. 3D Optical Mouse
Bus 002 Device 004: ID 17a0:0001 Samson Technologies Corp. C01U condenser microphone
Bus 001 Device 007: ID 03f0:3d17 Hewlett-Packard LaserJet P1005

Ok some more info. For some reason if i have made the text large in the document i want to printer the HPLIP is no help. It will only printer the text small. I also in order to printer via the HPLIP i have to import it in. There is a wizard to do so and only some file types work. The file type for the writer app i use doesn't work so i have to convert/saveas *.txt. A pain in the bum to do all this but works everytime. You may also have to replug the usb cord at the back of the computer every session too. I know there was something else but have forgotten it now. Would love it if someone can think of some way that the firmware stays in place as i dont'  know anything about this type of thing

---

### Post by rapattack1 on 2013-06-25
[ATTACH=CONFIG]244121[/ATTACH]
I downloaded an update and this is one of the things that i noticed went wrong

---

### Post by grandad67 on 2014-05-23
Thankyou so much for this - I got it to work.
 Though I was annoyed when, after LTS upgrade, it didn't. I thought upgrades brought improvements.
There's always the forum, thankyou -  grandad67

---

