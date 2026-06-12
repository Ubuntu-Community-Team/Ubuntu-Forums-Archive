---
title: "Staggering *bluetooth* mouse in Quantal Quetzal"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by eltonw on 2012-10-21
I did a fresh, clean install of **12.10** a day ago, on my Asus EEE 1000 PC and I keep getting various applications crashing. 

My most troubling problem is that my [COLOR="Navy"]bluetooth mouse[/COLOR] would start 'staggering' or become 'jittery'.
  

Partitioning was done as follows:
/dev/sda: divided into sda1 (7.5 Gb) mount point: /
with the _swap partition of 567 Mb_ at the end of the partition [COLOR="Navy"](surely that is adequate?)[/COLOR]
/dev/sdb: is completely allocated as: /home.

By default, the mouse and pointer sensitivity are at the minimum.

FWIW: The problem is intermittent, but frequent enough that I often have to resort to using the touchpad which is / has always been much too sensitive. As such, I preferentially use a mouse.

I suspect it might be related to **[COLOR="Navy"]bluetooth[/COLOR]**. With a USB mouse,this does not occur, but I would rather use the bluetooth one, so that the USB ports available for other devices.

Is there some way to correct this? 
TIA

---

### Post by Cheesemill on 2012-10-21
Just to check, have you tried new batteries in your mouse?

---

### Post by zuccster on 2012-11-01
Same issue here.  Bluetooth mouse behaves until suspend resume, then 'pauses' for ~0.5 secs every ~2 secs.  Touchpad unaffected.

---

### Post by smurfzilla on 2013-02-13
+1 to that - my logitech bluetooth travel mouse worked fine with old HP laptop and 12.04 (that had been upgraded from like 10 to 11 to 12) clean install of 12.10 on Elitebook 8570w has severe mouse "dragging" issues - mouse follows really slowly and then catches up and is ok and then just drags.

---

### Post by eltonw on 2013-05-11
> **Cheesemill said:**
> Just to check, have you tried new batteries in your mouse?
First of all my apology for such a long delay in replying. For some strange reason gmail is finding 'unread' emails here and there going back to DECEMBER 2012!.  :confused:
THANK you and others for your comments. and YES, it does appear that if the battery is starting to fail, further clicks of the mouse buttons can cause the entire system to abend. (NOT tested or confirmed in Ubuntu 13.04, however)

---

