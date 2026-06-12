---
title: "USB 2.0 with Hardy"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by mack1408 on 2008-06-24
I'm completely new to the Ubuntu world, and recently installed Ubuntu (8.04 server edition) on an old Pentium 1.4 system with about 640 MB of RAM, and it has worked great.  After the install I put in an Iogear USB 2.0 PCI controller card (to be used with an external hard drive), but it doesn't seem to be transferring at anything faster than 1.1 speed.

Is there any way to make sure that Ubuntu sees the card as 2.0?  I think that the modules needed are present and loaded (echi-hcd...?), but can't be sure.  Has anyone had experience with getting USB 2.0 to work correctly?

---

### Post by cuby on 2008-06-24
Note that USB work is done by the processor and not by the pci interface (in firewire the controller would be in the card). Is your computer under high load?

Did you check if the pci card is USB 2.0 full-speed or hi-speed?... see: [http://arstechnica.com/news.ars/post/20031003-2927.html](http://arstechnica.com/news.ars/post/20031003-2927.html)

---

### Post by mack1408 on 2008-06-24
According to Iogear, it is a hi-speed card.  Is there a way to watch CPU load in Linux while a transferring a file using the card?

---

### Post by cuby on 2008-08-18
sorry for the delay.
open a console and execute: top
It will show you the computer activity.

---

