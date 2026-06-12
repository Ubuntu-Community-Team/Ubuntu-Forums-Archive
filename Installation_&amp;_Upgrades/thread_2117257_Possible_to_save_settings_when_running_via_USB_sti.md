---
title: "Possible to save settings when running via USB stick?"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by ubuntark on 2013-02-18
I have been running 12.10 from a USB memory stick ( 8 GB) --- is it possible to shut down and restart and save any and all changes right on to the stick?  And then fire up in the same computer?  Or how about in another computer?  


thank you for the help

---

### Post by TenPlus1 on 2013-02-18
If you use the Startup Disc Creator that comes with Ubuntu and create a persistance file while doing this it wil let you save changes when you boot from your live usb flash drive...

---

### Post by C.S.Cameron on 2013-02-18
There are several ways to save data and settings, the above is probably simplest.
You can also do a full install to USB drive, just like to internal disk.

---

### Post by sudodus on 2013-02-18
> **TenPlus1 said:**
> If you use the Startup Disc Creator that comes with Ubuntu and create a persistance file while doing this it wil let you save changes when you boot from your live usb flash drive...
+1

Yes this is possible. It is even possible to create a partition with an ext4 file system (instead of a file). Just give it the label **[FONT="Courier New"][SIZE="3"]casper-rw[/SIZE][/FONT]**

It is also possible to make a 'regular installation' to a USB drive. 8 GB is enough at least for Lubuntu and Xubuntu. I have such a system. The only problem is that updating is slow, because writing many small files via USB 2 is very inefficient. But with USB 3 it will be much faster.

---

