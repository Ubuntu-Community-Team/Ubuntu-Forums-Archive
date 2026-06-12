---
title: "Install Ubuntu from USB stick without boot"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by myfunkystar on 2010-06-06
I have an existing instalation of Ubuntu Server 10.04 on an old machine with no floppy, cd-rom (broken after I did the install)
I want now to make a fresh install from a USB stick but it can't boot from USB.
Can I install using the terminal from my USB stick?
 
Thank you!

---

### Post by sXeChris on 2010-06-06
Although this is rather old, I hope it helps:
[http://www.pendrivelinux.com/usb-x-ubuntu-610/](http://www.pendrivelinux.com/usb-x-ubuntu-610/)

---

### Post by madalasatish on 2010-06-06
To install Ubuntu server edition from USB stick you should create STARTUP disk. 
ISO image wont work on USB.  You can create a start up disk from an ISO image easily at    SYSTEM>ADMINISTARTION>START UP DISK CREATOR.

---

### Post by myfunkystar on 2010-06-06
Even if I already mentioned it , my old machine dosen't have an option in bios to make it boot from USB, so it can't boot from an USB stick. It also can NOT boot from a cd-rom or a floppy disk because they are missing.
Fortunately this old machine already has Ubuntu Server installed on it. Can I install a fresh Ubuntu Server somehow? Considering that I have 2 usb ports I think this can be achived with an USB stick, but how?
 
Anyways thank you for the fast replys.

---

### Post by C.S.Cameron on 2010-06-06
You can download the iso and use UNetbootin to make like a virtual CD on your hard disk that will allow you to install Ubuntu the next time you boot.

I guess you can do the same if you have the iso on USB stick.

---

### Post by cagey_cretin on 2010-06-21
> **madalasatish said:**
> To install Ubuntu server edition from USB stick you should create STARTUP disk. 
ISO image wont work on USB.  You can create a start up disk from an ISO image easily at    SYSTEM>ADMINISTARTION>START UP DISK CREATOR.
Sadly, I have a FUBARed 8.10 install. My other machine, also and 8.10, does not have the "start up disk creator". Disappointing to be sure...

As an aside, I tried upgrading my FUBARed machine to 9.something, and never got the display back, hence the desire for a USB install.

---

