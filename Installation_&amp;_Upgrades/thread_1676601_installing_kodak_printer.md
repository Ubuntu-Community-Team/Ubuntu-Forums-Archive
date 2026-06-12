---
title: "installing kodak printer"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by steamman1 on 2011-01-27
I am trying to install a Kodak Printer to my Ubuntu10. Only to be informed that the CD  autorun is not supported in files, I have the printer installed on the windows OS, without any problems, I have explored the CD and even tried setup but with no joy.
Has any member encountered similar probs with installing software.

thanks for any assistance Steamman1

---

### Post by Mark Phelps on 2011-01-27
The files on the CD are most likely for MS Windows only -- so even it you could get the autorun to work, that would not do you any good.

You can't install Windows printers in Linux, even though some folks might tell you that Wine will do it -- it won't.  Wine can not be used to install Windows drivers.

So, basically, what you need to do is plug in the printer and then go into the Printer dialog in Settings to see if it has been detected.  IF it's a USB printer, it should be detected.

Then, use the menu options to complete the printer installation.

You could also open a browser and enter "localhost:631".  That will open CUPS, and from there, you can install and manage printers.

---

### Post by steamman1 on 2011-01-29
> **Mark Phelps said:**
> The files on the CD are most likely for MS Windows only -- so even it you could get the autorun to work, that would not do you any good.
 
You can't install Windows printers in Linux, even though some folks might tell you that Wine will do it -- it won't. Wine can not be used to install Windows drivers.
 
So, basically, what you need to do is plug in the printer and then go into the Printer dialog in Settings to see if it has been detected. IF it's a USB printer, it should be detected.
 
Then, use the menu options to complete the printer installation.
 
You could also open a browser and enter "localhost:631". That will open CUPS, and from there, you can install and manage printers.
 
 
 
Many thanks Mark I shall keep you informed.I shall try your suggewstions
Would the same method apply to any Windows application software

---

### Post by paulnewall on 2011-01-29
There is a driver here
[https://sourceforge.net/projects/cupsdriverkodak/](https://sourceforge.net/projects/cupsdriverkodak/)

---

### Post by steamman1 on 2011-01-30
I have done the Cups config and entered the Kodak ESP 3200 series,followed the info but cannot seem to get anywhere. 
i am not certain as to how to follow the configuration and wonder if you could do a demo as to how to install from CD.
many thanks steamman.

---

### Post by Julieskey on 2011-11-29
I had the same problem as steamman1.  Kodak informed me that they could not locate a CUPS driver for the ESPOffice 6150. They were wrong. Followed Mark Phelps advice and my Kodak printer works beautifully with my Ubuntu operating system.  It is so nice not to be beholding to Microsoft!

---

### Post by paulnewall on 2011-11-30
It was that easy because ubuntu 11.10 now includes the cups driver.
For earlier ubuntus you need to install the driver.

---

### Post by paulnewall on 2012-01-14
There is now a basic scanner driver, works much better with WiFi than USB though.
[http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/]("http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/")

---

