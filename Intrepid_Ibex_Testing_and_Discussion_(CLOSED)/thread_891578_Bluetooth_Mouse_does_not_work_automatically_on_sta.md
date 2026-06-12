---
title: "Bluetooth Mouse does not work automatically on startup"
date: 2008-08-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by saracen on 2008-08-16
I have a Logitech MX Laser Bluetooth mouse.  Whenever I restart my laptop, the mouse does not work automatically.  I have to remove and re-insert the USB bluetooth dongle to get it to work again.

This does not happen with Fedora.  Does anyone know of a fix?

---

### Post by saracen on 2008-08-17
bump

---

### Post by Ozdemon on 2008-08-17
You might want to look at this:
[http://ubuntuforums.org/showthread.php?t=227057]("http://ubuntuforums.org/showthread.php?t=227057")
and the threads mentioned within.

I had the same problem, but not anymore (except occasionally after installing some software).

---

### Post by saracen on 2008-08-20
When I run 'hcitool scan' the mouse does not show up.

I have a feeling that command is being interpreted by the built-in bluetooth adapter on my laptop, not the external USB bluetooth adapter for the mouse.  When I run hciconfig all I see is hci0, which is built-in device not the one for the mouse.

I am wondering how this works out of the box on Fedora and why the mouse works when I remove and re-attach the USB bluetooth adapter for the mouse after the system boots... :confused:

---

### Post by Ozdemon on 2008-08-20
Just before you run hcitool scan, press the connect button on the bottom of your mouse.  The mouse will start flashing.  It will then be picked up on the scan.

---

### Post by esoleyman on 2008-08-20
Install **bluez-input AND bluez-gnome** packages and use the the GNOME bluetooth applet to connect your mouse to the system.
[INDENT]
* Right click on the Bluetooth icon
* Choose **Browse Device**, then the device
* Select **Connect**[/INDENT]


To make this connection trusted and permanent

[INDENT]* Right click on the Bluetooth icon
* Choose **Preferences**
* Select the *Bonded Device* at the bottom of the window
* Select *Set Trusted*
[/INDENT]
There's no need to muck around on the command line or through any of the /etc/bluetooth/* and /etc/default/bluetooth files to make this work anymore.

---

