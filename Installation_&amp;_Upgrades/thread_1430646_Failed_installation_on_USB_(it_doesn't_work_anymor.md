---
title: "Failed installation on USB (it doesn't work anymore!)"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by kronos34 on 2010-03-15
Hi all, 

I'll describe my problem with the USB installation I just had.

I was trying to make a persistent USB pen-drive, so I booted my desktop computer with the 9.04 live CD and started to install it in the USB disc (8Gb). I chose the by default partition option and waited patiently while sipping tea... until an error window pop out. 

I cannot remember the exact error but it was a read-only sort of. The system recommended me to clean the lense, change my disc, etc. I booted again my Ubuntu at the desktop and tried to read the USB pen, but it couldn't be mounted. 

So I tried to format it with my XP. The pen was recognised, I prepared the formatting options, but the system returned me again a read-only error. It couldn't be formatted! 

Do you think of any way to recover the USB? What could be the error with the installation? :(

Thanks!!

---

### Post by thegod_slayer on 2010-03-15
i can't understand your problem but you can try inserting your pendrv
in a system having ubuntu installed in it.
then you can fully format the pendrv there.
i hope it will work......

---

### Post by kronos34 on 2010-03-16
Thanks. I have been trying different tests as proposed in several forums, but none of them worked out.

1) I try to format in XP, but it cannot be formatted
2) the pendrive does not have any external switch for read-only mode
3) I could find different recover programs on internet that can access the pendrive. I can recover the files; but still the pendrive cannot be formatted.
4) I tried to modify the registry at XP to put WriteProtect=0, but it also fails.
5) XP cannot execute the "hard disc error" utility on the pendrive.  

Moreover, if I try to mount it on my desktop Ubuntu, it gets a mounting error so I cannot access the pendrive. I think I will try other possibilities on Ubuntu because I think I cannot go further on XP, but I'm a newbie on Linux so I still have many doubts.   

Maybe the pendrive is broken (a couple of weeks old device, anyway). But I don't know how the installation of Ubuntu could destroy the pendrive. A faulty device? 

thanks anyway...

---

### Post by thegod_slayer on 2010-03-16
i hope there was no problem in installation
but somehow the pendrv got removed while data was being transferred.
as you see hard disk drives (external or internal) can have problems if they are removed manually or force fully while data transfer.
(i myself was a victim of this. my transcend 4gb got an fatal error while my kid brother removed it while i was transferring some movies)
i hope your pendrv hasn't got any fatal error.
hope it works fine.
best of luck.
but if your pendrv has got a fatal error then you can get it replaced from the company , if it is in the warranty period.

best of luck though.

---

### Post by wilee-nilee on 2010-03-16
In Ubuntu you don't want the USB mounted to reformat it in gparted, it would not format while mounted. Try Ubuntu again and look at the USB with gparted delete the fat32 and reformat it.

---

