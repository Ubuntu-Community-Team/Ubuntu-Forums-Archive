---
title: "usb connected printing Karmic Koala 9.10"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Charlemagne1st on 2009-09-06
I use usb connected lexmark printers. These work with the lexmark z600 driver.
One is connected to a Debian 5.0 server and the other I use as a deskside printer that I plug in to my laptop (Ubuntu 9.10 2.6.31-9-generic). 

Since the upgrade to cups 1.4 the z600 driver has stopped working. 
I believe that the way usb connected printers are handled has changed, but I don't know enough about usb to fix this.

I believe the z600 driver has stopped working because the usb file system is not mounted under ubuntu 9.10.

On the Debian 5 Lenny system, the usb file system is mounted on /proc/bus/usb 

when I try to mount the usb file system under Karmic Koala 9.10 I get 

mount: mount point /proc/bus/usb does not exist

This failure I believe is caused by kernel usb modules not being present - but I don't know how to progress. Can anyone advise me about usb in 9.10?

---

