---
title: "toshiba laptop install problem"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by numbers1thru9 on 2007-02-09
I have a toshiba laptop model p105-s6177 i just got two days ago. It has a sata hard drive in it and im trying to install edgy. I keep getting errors like PCI: Cannot allocate resouces at bridge or Buffer I/O error on device sr0, logical block whatever. does anyone know something i can do to get it to install and run properly?

---

### Post by k0rv3n on 2007-02-09
I have the same problem with a Toshiba Satellite P100-208 that I got yesterday.
Had to install windows :(

Anyone know what to do?

---

### Post by mikewhatever on 2007-02-09
If these are the errors you get, 
> [17179570.848000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.848000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.848000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.848000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.848000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.848000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.848000] PCI: Cannot allocate resource region 0 of device 0000:06:00.0

it should not prevent the installation. Apparently, a lot of people reported them on various laptop models. Could you, possibly, elaborate, why you can not install.

---

### Post by numbers1thru9 on 2007-02-09
im getting that exact error, but after that the spash screen with the scroll bar comes up and when it goes away i get the error with the sa0 device which im assuming that is my sata hd, it then just keeps giving the same errors and never actually loads a gui.

---

### Post by k0rv3n on 2007-02-10
Okey so it worked to install. During install the comp just got stuck at all the errors. But after I pressed crtl+alt+del it sent some kill signals to what ever got stuck and continued with the install. Now after installation I still get the errors but it doesn't get stuck!

Still a bit annoying thou

---

