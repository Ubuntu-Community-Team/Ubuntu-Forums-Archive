---
title: "Error when trying to install .BIN file"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by RealGomer on 2010-09-17
I'm trying to load the drivers that came with my wireless-n usb adapter. The file is rt2870.bin. 
I ran cmod a+x rt2870.bin command in terminal just fine. 
When I try to run sudo ./rt2879.bin I get an error message 1: Syntax error: word unexpected (expecting ")"). 
The .bin file came from the wireless adapter manufacturer.
Am I missing something? Should the cmod be run under sudo as well?
This device ran just fine before my router got funky. I finally got my 3 windoze boxes to connect, one using the same adapter as Ubuntu.

---

### Post by Lateralis on 2010-09-17
A .bin is not a native Linux file type (as far as I'm aware at least).  Moreover, the drivers which come with these sorts of things are unlikely to be Linux compatible.  

So, what you did was change the permissions of the file so that anyone can execute the file.  However, the file isn't an executable that the Linux environment understands, which is why it threw a hissy.  

Anyway, a quick google search leads me to think that you are using the Ralink rt2870 wireless adapter?  You may want to check out the [Ralink website]("http://www.ralinktech.com/support.php?s=2") which contains Linux drivers.  You may also want to check out [this]("http://ubuntuforums.org/showthread.php?t=1476007&highlight=Ralink+usb+wifi") Ubuntu forum link regarding the 2860 chipset; may not be directly applicable but will doubtless be of interest/use.

---

