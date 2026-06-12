---
title: "Internet VIA USB device from mobile company"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by asbani on 2010-11-07
Hello everybody, I just did install to the ubuntu, everything is fine, now I want to ask you good people to help me with my problem, when I installed ubuntu i wasn't thinking ahead. 

I have an internet from my mobile company, it isn't ethernet or a usb thats connected to a phone or anything. its basicaly a device that has my mobile card/chip inside and it connects to the internet, here's a picture of the device to give more information.

[http://3.bp.blogspot.com/_FAAk_63R9Lg/SKlo67OI5fI/AAAAAAAABCQ/YLa9YziBkvg/s1600-h/ddf.jpg](http://3.bp.blogspot.com/_FAAk_63R9Lg/SKlo67OI5fI/AAAAAAAABCQ/YLa9YziBkvg/s1600-h/ddf.jpg)

Basicaly on windows xp, or 7, I just plug this into any USB then it automatically installs a software, then program will popup that has "Connect" buttom, I click on that and i'm online, but in linux/ubuntu that auto installation is not coming.

so my question here, is there a software out there to make this internet works for me? have anybody of you guys had similiar type of internet and got it working? Please help me


P.S. please please forgive my poor english, It's not my native language, and I do know it sucks.


thanks in advance.

---

### Post by punkybouy on 2010-11-07
With the device connected go to a terminal window in Ubuntu and type "lsusb" without the quotations and paste the output in a window so we can identify the chip used.  And your English is actually pretty good.

---

### Post by punkybouy on 2010-11-07
If you could identify the Windows driver installed with Windows you might be able to connect using a linux program called ndiswrapper. The Windows driver would have a .inf file and maybe a .sys file. I used a Windows wifi driver for several years using ndiswrapper on an old Dell laptop.  If you can find all the windows software for your dongle put them on a usb thumb drive then copy them to a directory on your Ubuntu installation.  Start ndiswrapper and click the "add" button and navigate to the directory where you put all the software.  Hopefully there will be only one file with a .inf extension.  Ndiswrapper might activate the driver.

---

