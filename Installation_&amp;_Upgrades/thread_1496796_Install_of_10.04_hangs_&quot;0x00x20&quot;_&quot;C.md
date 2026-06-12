---
title: "Install of 10.04 hangs &quot;0x0/0x20&quot; &quot;Child_rip&quot; on Toshiba Pro L510 with InsydeH20 bios"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by Dave Gravox on 2010-05-29
The installation of 10.04 hangs on this computer with 64bit install. Doesn't get to the menu options. Simply hangs on terminal like output ending "0x0/0x20" "Child_rip". I have tried the 64bit install via usb, CD-ROM, Wubi, plus the alternative installer all with the same result. The ISOs I have used all work on other machines. 9.10 also hangs on a blank screen after choosing the 'try once' option from the menu.

Toshiba Satellite Pro L510 (PSLGXA-002002)
Core i3 2.13 330M 
ATI Mobility Radeon HD 5145
InsydeH20 BIOS v1.1 EC: v5.29
4GB RAM, 320GB HDD

Does anyone know what the issue is here?

---

### Post by davidmohammed on 2010-05-29
is this a 64bit processor or 32bit - have you tried 32bit lucid?

---

### Post by davidmohammed on 2010-05-29
... there is also a recent thread for a similar model as yours - a l505

possibly you are affected by this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/472183") - there seems to be a fix available...

---

### Post by DarwinSurvivor on 2010-09-03
Just installed on a friends Satelite L650 and it didn't work. Then I found that toshiba's website has a BIOS update for the machine. Installed that and BOOM, worked perfectly.

---

