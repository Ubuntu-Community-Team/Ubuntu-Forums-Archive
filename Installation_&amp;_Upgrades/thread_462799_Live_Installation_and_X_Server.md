---
title: "Live Installation and X Server"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by redw0lf on 2007-06-03
Hi,
I have been having issues trying to install Ubuntu 7.04 on my Asus Laptop (A600KT). I have added the line
```
irqpoll pci=noacpi noapic nolapic acpi=off
``` 
from  [https://help.ubuntu.com/community/Installation/32bitonAMD64](https://help.ubuntu.com/community/Installation/32bitonAMD64) to allow ubuntu to boot since it would previously just hang with a blank black screen without the extra options.
After I press enter for the option "Start or install Ubuntu" there is an intermittent error reads
```
[    139.396491] bcm43xx : Error : Microcode "bcm43xx_microcode5.f" not available or failed.
```
After this appears a couple of times, a blue screen appears with "Failed to start the X server ( your graphical interface)....". After pressing enter for more information, there is a line "Fatal server error: no screens found" While this is being displayed, the existing text from the X server error is being overwritten by the bcm43xx error, and after a few minutes, the entire screen is filled with the bcm43xx errors and the X server errors can not be seen.

The laptop is AMD64 Turion MT34 and is widescreen.
Thanks for any help

---

### Post by hellmet on 2007-06-03
Google gave me a few results,  all about laptops, but nothing related to installation problems. Its a problem with your WIFI card. I'm not too familiar with Laptops, so just see if you can turn off WLAN card before trying to install ubuntu..

---

### Post by hellmet on 2007-06-03
Similar threads. You should have searched. :D . Lots of results on our forums. Is that a Broadcom wireless card?

[http://ubuntuforums.org/showthread.php?t=460310&highlight=bcm43xx_microcode5](http://ubuntuforums.org/showthread.php?t=460310&highlight=bcm43xx_microcode5).
[http://ubuntuforums.org/showthread.php?t=461302&highlight=bcm43xx_microcode5](http://ubuntuforums.org/showthread.php?t=461302&highlight=bcm43xx_microcode5).
[http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx_microcode5](http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx_microcode5).

There are also plenty of threads. Just search for . 
bcm43xx_microcode5.f

---

