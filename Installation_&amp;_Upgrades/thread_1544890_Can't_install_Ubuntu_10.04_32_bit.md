---
title: "Can't install Ubuntu 10.04 32 bit"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by lucacerone on 2010-08-03
Dear all,
I'm trying to install Ubuntu 10.04 (32 bit)
on my laptop (where currently is installed the amd64 version of Ubuntu 10.04
that I've decided to remove because of some small issues).
I've tried using the installation CD (the same I've used to install
it on my desktop, so I know that is a working copy),
but at boot, although I select to boot from CD, the Live version doesn't
start and Ubuntu 64 is run as usual.
I've tried to create a startup diskon a usb pen,
there the live version seems to start but then Busybox 1.3 is loaded
and there is an error with initfrm saying that no operating system 
can be found.
Any advice on how to solve this situation?
It would mean a lot to me to install the 32 bit version.
I've been told to download the alternate edition, but I'm still
downloading it, in the meanwhile if you've any other advice it's really
appreciated!
Cheers, 'Luca

---

### Post by alenn on 2010-08-03
did you set your first boot device, it must be CD-ROM or USB, depending which media you use

---

### Post by lucacerone on 2010-08-03
> **alenn said:**
> did you set your first boot device, it must be CD-ROM or USB, depending which media you use
Hi alenn.
Yes I boot from the right device, I choose it at startup with two different results
(as I've tried to explain, sorry if my English in not this good):
1) booting from CD doesn't load the live version at all, and the installed OS is run;
2) booting from the usb pen, seems to start the live session, but it doesn't, in fact a black screen saying that I'm in Busybox appears.

Both the CD and the USB PEN work fine, I've tried the CD on other machines and it works. Have really no clue of what's going on.

Cheers, -Luca

---

### Post by alenn on 2010-08-03
> **lucacerone said:**
> Hi alenn.
Yes I boot from the right device, I choose it at startup with two different results
(as I've tried to explain, sorry if my English in not this good):
1) booting from CD doesn't load the live version at all, and the installed OS is run;
2) booting from the usb pen, seems to start the live session, but it doesn't, in fact a black screen saying that I'm in Busybox appears.

Both the CD and the USB PEN work fine, I've tried the CD on other machines and it works. Have really no clue of what's going on.

Cheers, -Luca

try to reset your bios on default and then try again

---

