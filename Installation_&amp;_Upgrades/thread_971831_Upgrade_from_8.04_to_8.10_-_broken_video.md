---
title: "Upgrade from 8.04 to 8.10 - broken video"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by thatsdm2u on 2008-11-05
I had a working installation of 8.04 on a Everex Stepnote NC1510, but after the upgrade to 8.10, I have having serious video issues.  The splash screen shows as normal, but then the login fails to load.  I get a corrupted looking graphic for the mouse pointer for just a brief moment before a white screen lockup.  Not sure which logs (if any) would help to solve this, but I am hoping that someone can help me (I have been learning more about linux and I am loving it, but not quite savvy yet).

---

### Post by dickohead on 2008-11-09
Does your computer have an ATI based graphics card?

Try this: [http://ubuntuforums.org/showpost.php?p=6129000&postcount=12](http://ubuntuforums.org/showpost.php?p=6129000&postcount=12)

---

### Post by portals on 2009-03-05
Everex NC1510 notebooks use the VIA Chrome chipset.  I'm having problems loading "Intrepid" 8.10 as well.  Had no problem when I used Fiesty.  Something was changed, obviously.  

I also now start getting the 8251 not tied to the I/O buss error message which I never got before.  Too bad.  Intrepid works great on my E-Machine desktops, and I absolutely hate the idea of going back to Vista on my laptop, but I have to have something that works.

I no longer have Fiesty.  The CD was destroyed.

---

### Post by Brian Lee on 2009-03-05
Can you check if the CDROM DMA has turn on? If your CDROM is shown as hdb that you can check by:

hdparm /dev/hdb

to get the result.

---

