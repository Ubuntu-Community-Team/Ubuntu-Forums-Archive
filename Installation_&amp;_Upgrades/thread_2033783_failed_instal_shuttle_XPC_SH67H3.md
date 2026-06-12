---
title: "failed instal shuttle XPC SH67H3"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by csgmtu on 2012-07-26
hello,

I have shuttle xpc SH67h3

8GB crucial ram
ASUS Blue ray 
Corsair SSD/Western digital scorpio blue laptop drive (I have tried both)

Intel i5-3570 CPU


I have installed windows 7 and it works OK
I cannot instal Ubuntu 12.04
I get I/O errors.
when I can instal, updates crash

any suggestions?

thank you

cg:)

---

### Post by patg7590 on 2012-07-27
> **csgmtu said:**
> hello,

I have shuttle xpc SH67h3

8GB crucial ram
ASUS Blue ray 
Corsair SSD/Western digital scorpio blue laptop drive (I have tried both)

Intel i5-3570 CPU


I have installed windows 7 and it works OK
I cannot instal Ubuntu 12.04
I get I/O errors.
when I can instal, updates crash

any suggestions?

thank you

cg:)

(I am working on this machine with the OP)

We have also qualified the ram, 14 passes with memtest. 
Ubuntu 12.04 gives i/o errors on install from Desktop CD or live usb (amd64). Alternate amd64 image gets it installed, but as soon as there is any disk access (updates) they all start to fail and crash. Shuttle support says they have only tested it to 10.04 (the previous LTS). These issues are present on an SSD and a 2.5" 250gb hdd. We have tried the SATA2 and SATA3 ports, different sata cables, everything we can think of.

I don't believe the issue is hardware related, as Windows 7 x64 Professional works just fine. 

Are there any other Shuttle owners that can speak to this? Is this a hardware incompatibility issue? Is this an Ubuntu bug? Where should we go from here? We are going to try installing some other distros, but I assume if this issue is present in Ubuntu it will be in Mint as well, hopefully not in Debian, which is what we might have to end up going with, since 10.04 is getting old. 

Help appreciated!

---

### Post by BooToo on 2012-08-07
And... here is #3 unhappy owner of an SH67H3 with Ubuntu install issues...

I tried to install it on it today and got the first time a "fatal error" message related to the launcher (Gubt or something like that)...

I tried a second install from scratch who succeed but after the reboot, I ended up with a black screen and a flickering prompt(not even the usual error message when it cannot find an OS).

I email the Shuttle tech support tonight to find out what is going on with Ubuntu support...

Soooooo disappointed by my purchase... I have to live with win 7 (which by the way installed like a charm...) for an undetermined period of time...

I'll keep you posted :confused:

---

