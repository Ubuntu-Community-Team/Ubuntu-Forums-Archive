---
title: "[SOLVED] Problem with Epson DX7000F printer"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Norber_OK on 2008-07-10
I have the Ubuntu 8.04 version (hardy heron) and Epson Stylus DX7000F usb printer. I got it work.

The problem was that from rebooting it didn't work any more, and I don't remember what I did to get it work.

Things that could help:
.- I got it work installing the scx6900f avasys drivers for redhat and the sources and compiling them in my pc
.- I have no /dev/usblp0 no /dev/usb/lp0 and no parallel ports.
.- I think I remember that I did get a /dev/usb/lp0 and then it worked.
.- On [http://localhost:631/printers/](http://localhost:631/printers/) I'm getting "/usr/lib/cups/backend/ekplp failed" message.

Please, any idea, workaround, etc?

---

### Post by wpshooter on 2008-07-10
May I ask if all of this is really necessary ?

Is there not a driver for your Epson Stylus DX7000F already included with and installable from with in System/administration/printer ?  Have you looked at the listings for Epson printers ?

---

### Post by Norber_OK on 2008-07-12
Yes, of course, all of this is really necessary.

No, there is not a driver for my Epson Stylus DX7000F already included with and installable from with in System/administration/printer. There is a CX7000F driver but not a DX7000F driver and not a CX6900F driver.

Any idea, workaround, etc ...?

---

### Post by Norber_OK on 2008-07-12
Perhaps that is not necessary to install the avasys drivers if the CX7000F one that comes with Ubuntu is valid for my DX7000F printer. So I have to test it, but I have another problem:

On "System -> Administration -> Printers -> New Printer" I have NO USB device to chose.

What should I chose?

---

### Post by hansdown on 2008-07-12
Hi norber_ok. I,m fairly new,so my help to offer is very limited. Can You go to system>preferences>hardware testing? Just a thought.

---

### Post by Norber_OK on 2008-07-12
Yes, I can, and I have done it as you suggest (system>[COLOR="Red"]administration[/COLOR]>hardware testing), but it says nothing about USB.

Any idea, workaround, etc..?

---

### Post by Norber_OK on 2008-07-13
I want to test the CX7000F printer driver that comes with Ubuntu with my DX7000F printer but I have one problem:

On "System -> Administration -> Printers -> New Printer" I have NO USB device to chose.

What should I chose?

I have tried to put "usb://epson/Stylus%20CX7000F" in the device uri but it does not work.

Any one has an idea about what can I chose?

---

### Post by wpshooter on 2008-07-13
Have you looked at this page ?

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX7000F](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX7000F)

When are you plugging the printer into the computer ?  Before booting or just prior to doing the setup once you get up to the desktop.  I think perhaps when you plug the USB cable in might make a difference.

Good luck.

---

### Post by Norber_OK on 2008-07-13
> **wpshooter said:**
> Have you looked at this page ?

[http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX7000F](http://openprinting.org/show_printer.cgi?recnum=Epson-Stylus_DX7000F)



I have looked, then I have downloaded gutenprint-5.2.0-beta3 from sourceforge.net, and then I have compiled it.
Then I have the Epson Stylus DX7000F printer option :-) but I think I have putting wrong the device uri when I'm trying to add the printer in CUPS ([http://localhost:631/admin](http://localhost:631/admin)) because it says:

Bad device-uri "USB://EPSON/Stylus%20DX7000F"! :-(

> **wpshooter said:**
> When are you plugging the printer into the computer ?  Before booting or just prior to doing the setup once you get up to the desktop.  I think perhaps when you plug the USB cable in might make a difference.

Good luck.

I have the printer plugged all the time.

Any idea about the correct device uri?

---

### Post by Norber_OK on 2008-07-14
In cups web, when adding a new printer and it asks me about the connection it gives me a list in which I can chose NO USB backend (because it doesn't appear in the list), so I'm choosing AppSocket (for example) and in the next step, when it asks me the connection uri I was deleting the word "sockect" and I was writing: "usb://epson/Stylus%20DX7000F" then it allowed me to continue till the end where it stopped with the uri error:   Bad device-uri "USB://EPSON/Stylus%20DX7000F"!

Now I have tried to write "epson:/Stylus_DX7000F" then it allows me to continue till the end without an error, but when I go to printers tab it shows me the message:

"Unable to open parallel port device file: No such file or directory"

What shoul I try?

---

### Post by Norber_OK on 2008-07-16
SOLVED: See [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=940149](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=940149)

---

