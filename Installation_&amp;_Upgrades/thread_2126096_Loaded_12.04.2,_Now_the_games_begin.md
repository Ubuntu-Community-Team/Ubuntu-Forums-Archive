---
title: "Loaded 12.04.2, Now the games begin"
date: 2013-03-16
forum: Installation &amp; Upgrades
---

### Post by alvinmoneypit on 2013-03-16
Since loading 12.04 LTS, I wondered what challenges it would create.  It seems I cannot print until I solve the "driver riddle".  I have an old Lexmark 1150 which I used a Z600 driver for which gave acceptable printing under 10.10.  It looks like for 12.04 this is not good enough.  12.04 offers a driver for my 1100 series Lexmark, but refusess to download it since the sources "Is not trusted".   (So why offer it?)

So once again with the security:  How do I access the security prefs so I can trust the source, or gain enough access to load my z600 drivers which I have ppd, deb, and tar for?  Any response is appreciated.

---

### Post by darkod on 2013-03-16
Get a real printer, a real manufacturer. :)

Lexmark support & downloads section includes Linux section and when you select it doesn't display any drivers available. By the way, it does the same for Windows. Not sure if it has something to do with browser, Chrome, don't have IE to try. They can't even make a support page and they want to make printers. :)

See if something like this can help you:
[http://ubuntuforums.org/showthread.php?t=1915316](http://ubuntuforums.org/showthread.php?t=1915316) (thread/howto only one year old)
[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

---

### Post by alvinmoneypit on 2013-03-16
Yes, I've already tried and failed att both of these HowTo's.  The second one you offered was able to get to Step 9 of the 100 series instructions.  No luck unpacking the drivers from deb or tar files, have the ppd, cannot load any of them, either over ridden by OS 12.04 or not doing it right.  Older HowTo resulted in warnings that "Alien not running as root", and  something about the scripts.  These things make me consider that the OS is not allowing driver install, so I wonder where to access the settings.  I used my Lexmark before on 10.10 w/o this much trouble getting the driver to load.

---

### Post by alvinmoneypit on 2013-03-18
I got it working by using [this HowTo]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters") to locate the [Z600 driver]("https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters?action=AttachFile&do=view&target=lexmark.z600-0.4.deb") and the i386 libstdc++5 I got from Synaptic. First got libstdc++5, then downloaded the Z600 driver. Get the ppd file out of the driver package by simply clicking on the package and extracting the ppd with Archive Manager.
    Then I installed with the onboard printer installer- 1) select printer, click forward; 2) program searches for driver, click 'cancel' if it finds one, click "forward"; 3 "Choose Driver" screen comes up, click "Provide PPD file" navigate the browser lookup to where you extracted the PPD of Z600 and click forward. Then your printer is loaded and you can try to print. Hope this works for other seekers.

---

