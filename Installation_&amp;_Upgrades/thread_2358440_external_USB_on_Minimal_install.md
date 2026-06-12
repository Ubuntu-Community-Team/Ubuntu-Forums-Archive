---
title: "external USB on Minimal install"
date: 2017-04-13
forum: Installation &amp; Upgrades
---

### Post by sold13r on 2017-04-13
Hi all .

I have completed a Minimal Ubuntu Install ( using the Yakketty Minimal 64bit ISO ) , and followed this guide - 
[http://www.richud.com/wiki/Ubuntu_Minimal_KODI_Install](http://www.richud.com/wiki/Ubuntu_Minimal_KODI_Install) -  to give me a usable HTPC.
( i did NOT install - USBMOUNT - part of the guide , but not essential  , as it did not work for me )

I have 1 External USB HDD plugged in , and i edited the FSTAB  file, using the UUID of the drive.
I added the following 2 lines:
 
# STORAGE
UUID=c4fec6a9-621e-492d-89fb-880930039857     /media/Storage   auto    rw,user,auto    0    0

Everything works and boots - unless i unplug the USB DRIVE and try booting . The startup hangs at looking for the USB and sends me to a "Maintenance" option.

MY QUESTION : 
How can i setup the PC to boot , BOTH with and without the External drive plugged in ?

---

