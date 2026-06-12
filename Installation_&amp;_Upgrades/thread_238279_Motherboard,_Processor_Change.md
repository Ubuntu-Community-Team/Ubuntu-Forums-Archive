---
title: "Motherboard, Processor Change"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by Gorlist on 2006-08-17
Hi, just wondering - will I have to reinstall Ubuntu if I swap around my motherboard & processor? 

Regards!

---

### Post by encompass on 2006-08-17
well, it wouldn't hurt to try wihtout changing... odds are your ubuntu install will detect everything jsut fine... uless your moving to something like amd from intel, I would recomentd reverting to the simple 386 kernel then go up from there.
I would like to here...

---

### Post by Gorlist on 2006-08-17
Hi, ok will give it ago, thanks :)

---

### Post by djheadley on 2006-08-17
I moved from a 433Mhz Intel Celeron to a 1GHz Pentium III (moved all drives to new machine).  All I Had to do was reconfig Xorg and reboot.  Sorry I can't remember what the command is.  My machine booted into server mode (because it couldn't run X) and I typed in the commands and rebooted and have been going ever since.  BTW I dual boot and had to reboot WinME 6 TIMES.

---

### Post by encompass on 2006-08-17
GREAT...
the command is...```
sudo dpkg-reconfigure xserver-xorg
```
press enter for the defaults that you had before and then select what you want changed.
Glad to here that the change worked.  I guess you could have changed to vesa first.  But don't matter when you know how to do it in text mode anyway.
Congrants on your faster computer... you now have me beat.  I use 700 mhz and love it.

---

