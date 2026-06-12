---
title: "Reinstall ubuntu fully, inside ubuntu"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by Myke. on 2009-12-03
Hey. I installed ubuntu inside windows. But windows has stopped working (really dont care)
Now i wana remove the windows (i am dual booting) and keep or re install ubuntu to be my only operating system
Is there a simple way to do this?
(im a n00b but can follow instructions good lol)

---

### Post by raymondh on 2009-12-03
> **Myke. said:**
> Hey. I installed ubuntu inside windows. But windows has stopped working (really dont care)
Now i wana remove the windows (i am dual booting) and keep or re install ubuntu to be my only operating system
Is there a simple way to do this?
(im a n00b but can follow instructions good lol)

Being a wubi-install, if you erase windows, you also erase Ubuntu as it "resides" inside windows.  You can try to move it out of windows.  Here's a link (NOTE, I don't know what version Ubuntu you are using .... EDIT ... just saw KARMIC in your sig.  Don't know if this will work in Karmic.)

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

Have a working/tested back-up of your files before proceeding.

If you decide to do a fresh-install, boot into the liveCD and install.  In step 4, choose USE ENTIRE DISK and continue with the install.  That will erase windows as well as install GRUB in the MasterBootRecord (MBR).

Regards.

---

