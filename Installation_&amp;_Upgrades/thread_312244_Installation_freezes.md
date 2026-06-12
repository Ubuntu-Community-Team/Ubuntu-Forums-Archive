---
title: "Installation freezes"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by dj50 on 2006-12-04
Hello,

I've been trying to install Ubuntu 6.10 on my laptop, a Toshiba Satellite 4070CDS with the following configuration:

- Processor: Intel Mobile Celeron - 366 Mhz
- Mainboard: Chipset: Intel i440BX/ZX
- Memory: 192 MB SDRAM
- Video: Trident Cyber9525DVD
( [http://www.tridentmicro.com/videographics/showmodel.asp?pro=cyber9525dvd](http://www.tridentmicro.com/videographics/showmodel.asp?pro=cyber9525dvd) )
- Display: 13'' LCD
- CD-ROM: 24x - Model: TOSHIBA CD-ROM XM-1802D
- HDD: 4GB - split in 2 partitions: Primary: 1.5 GB FAT32; Logical: 2.5 GB
- No network adapter

What happens:
- I boot from the CD, and I select Start Installation
- When GNOME starts I see an error dialog:
"There was an error starting the GNOME Settings Daemon. Some things, such as themes, sounds or background settings may not work correctly. The last error message was: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. GNOME will still try to restart the Settings Daemon next time you log in"
- I hit the Close button and everything seems to work fine - I've started a couple of applications and they work
- I hit the Install icon on the desktop
- Then, after a little while a window labeled Install appears with no content whatsoever, and the system freezes (I can't move the mouse cursor, and there is no more reading from the CD or the HDD)

I've attached a picture with the last screen from the installation. Please also notice at the bottom of the screen there is an area which is garbled - that is present throughout the installation and also in older versions of Ubuntu I've tested on this laptop - I'm running at 800x600x60hz, but 56hz has the same effect. I would appreciate some feedback on this also.

Thanks.

---

### Post by ajgreeny on 2006-12-04
Not sure about your trident video card,which could be causing the garbled bit at the botom of the screen, but anyway at 192 MB ram you are a bit short for the live CD to work for installation.  Get some more ram if possible, but it's worth a try in any case.

Get a copy of the alternate install CD, install it and then when you are up and running do an install of xubuntu-desktop, which will work much better on a low spec machine. Even then you may find it is a bit slow with your cpu at only 366Mhz.

---

### Post by dj50 on 2006-12-04
Well, I just wanted to install it, no matter the performance, just to see what's new and fool around a bit.

---

