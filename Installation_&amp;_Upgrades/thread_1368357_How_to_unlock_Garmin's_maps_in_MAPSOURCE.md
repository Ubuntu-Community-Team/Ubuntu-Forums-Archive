---
title: "How to unlock Garmin's maps in MAPSOURCE ?"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Davidus on 2009-12-30
Hello !

Father Christmas offered me the electronic gadget which missed on my mountain bike, a GPS eTrex Legend Hcx which I connect on my ubuntu (9.10)

I also bought the detailed Garmin's map of my region on DVD  (TOPO) and installed Mapsource supplied with TOPO (v. 6.15.4) using wine (the version of wine which works, ie 1.1.27 as indicated on the wine website). I have 2 problems at the moment:

1- GPS unit is not detected by Mapsource (while it works fine with qlandkarte) even when I use the mass storage mode.

2- I can't unlock the Garmin's maps [IMG]http://forum.ubuntu-fr.org/img/smilies/sad.png[/IMG] So I can read only the global view of maps in Mapsource, with zero details. It is also impossible to import the maps in MapSource from the GPS unit (the .img is on the microSD card) in qlandkarte, it can't read Garmin's files.  To unlock the maps I need (1) the GPS unit connected and detected by MapSource (2) MapSource (3) the Garmin website and the communication module from Garmin. It is this set which does not work...

I was thus obliged to reinstall winXP using virtualbox and there everything works, but that satisfies me in no way.

Did anybody succeed under Linux to show Garmin's maps ??

Thank you for your help !

---

### Post by blur xc on 2009-12-30
> **Davidus said:**
> Hello !

Father Christmas offered me the electronic gadget which missed on my mountain bike, a GPS eTrex Legend Hcx which I connect on my ubuntu (9.10)

I also bought the detailed Garmin's map of my region on DVD  (TOPO) and installed Mapsource supplied with TOPO (v. 6.15.4) using wine (the version of wine which works, ie 1.1.27 as indicated on the wine website). I have 2 problems at the moment:

1- GPS unit is not detected by Mapsource (while it works fine with qlandkarte) even when I use the mass storage mode.

2- I can't unlock the Garmin's maps [IMG]http://forum.ubuntu-fr.org/img/smilies/sad.png[/IMG] So I can read only the global view of maps in Mapsource, with zero details. It is also impossible to import the maps in MapSource from the GPS unit (the .img is on the microSD card) in qlandkarte, it can't read Garmin's files.  To unlock the maps I need (1) the GPS unit connected and detected by MapSource (2) MapSource (3) the Garmin website and the communication module from Garmin. It is this set which does not work...

I was thus obliged to reinstall winXP using virtualbox and there everything works, but that satisfies me in no way.

Did anybody succeed under Linux to show Garmin's maps ??

Thank you for your help !

I'm an Edge 305 user, and no, I haven't been able to run Garmin apps in Linux and use Vista in VBox.

I wrote them an email requesting native Linux ports- maybe you should too.  The squeeky wheel gets the grease...

BM

---

### Post by Davidus on 2009-12-30
> **blur xc said:**
> I'm an Edge 305 user, and no, I haven't been able to run Garmin apps in Linux and use Vista in VBox.

I wrote them an email requesting native Linux ports- maybe you should too.  The squeeky wheel gets the grease...


OK, thank you for your experience ! So I'll follow your advice and send an e-mail to garmin (and maybe also going to have a squeaky little pee on their showroom here, in Paris).

If anybody have a better idea, you're welcome ;)

---

### Post by Davidus on 2009-12-31
Unlock done 8) I used the code provided by my windows version of MapSource. The soft works great using wine 1.1.27, but still refuse to communicate with the GPS unit while the native linux applications can do...

---

### Post by Bosluis on 2010-01-13
> **Davidus said:**
> 
1- GPS unit is not detected by Mapsource (while it works fine with qlandkarte) even when I use the mass storage mode.

2- I can't unlock the Garmin's maps [IMG]http://forum.ubuntu-fr.org/img/smilies/sad.png[/IMG] So I can read only the global view of maps in Mapsource, with zero details. It is also impossible to import the maps in MapSource from the GPS unit (the .img is on the microSD card) in qlandkarte, it can't read Garmin's files.  To unlock the maps I need (1) the GPS unit connected and detected by MapSource (2) MapSource (3) the Garmin website and the communication module from Garmin. It is this set which does not work...

Hi Davidus, I am using Mapsource 6.13.7 running under wine.  You can download a copy [here]("http://www.gawisp.com/perry/mapsource/").

I have a nuvi 310, and it when connected via USB, it is found by Mapsource.

If you click on the "Receive from device" icon you can download track, route maps and waypoints.  "send to device" icon can do the reverse, and will send your unlocked maps to the unit.  Instead of the icons, you can use the menu "Transfer" and the either send... or receive.....

When I click on the icon, Mapsource just finds the device for me!:D

Bosluis

---

### Post by rimo on 2010-04-22
Hello,
if you want that your gps is recognized by mapsouce try this. It worked for me.

In order to make the USB transfer work you should have the garmin kernel driver up and running. After plugging the GPS into the PC monitor dmesg for message telling on which device the GPS is mounted on. Should look like this
"""
ohci_hcd 0000:00:0b.0: auto-wakeup
usb 2-3: new full speed USB device using ohci_hcd and address 3
usb 2-3: configuration #1 chosen from 1 choice
garmin_gps 2-3:1.0: Garmin GPS usb/tty converter detected
usb 2-3: Garmin GPS usb/tty converter now attached to ttyUSB0
"""
after that make a simlink to this device in your wine/dosdevices directory
"""
ln -s /dev/ttyUSB0 com1 (make the link like 
"""
regards rimo

---

### Post by rimo on 2010-04-22
in case you pc doesn't recognize any gps, try in terminal with this

[I]sudo modprobe garmin_gps
[/I]

and later again

*dmesg*

you will get something like 
[ 5776.676407] USB Serial support registered for Garmin GPS usb/tty
[ 5776.676429] garmin_gps 5-1:1.0: Garmin GPS usb/tty converter detected
[ 5776.676519] usb 5-1: Garmin GPS usb/tty converter now attached to ttyUSB0
[ 5776.676538] usbcore: registered new interface driver garmin_gps
[ 5776.676540] garmin_gps: v0.33:garmin gps driver

than see my message above

regards

---

