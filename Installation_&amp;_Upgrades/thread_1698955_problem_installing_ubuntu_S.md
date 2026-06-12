---
title: "problem installing ubuntu :S"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by jose1522 on 2011-03-03
I was trying to install ubuntu but I have this message in the screen:

(process:373): GLib-warning **: getpwuid_r(): failed due to unknown user id (0)

stdin: I/O error
/init: line 7: can't open /dev/sr0: No medium found


This is the story:

I was trying to install ubuntu on a partition of my hard drive but some reason I was not able to boot the OS from either the DVD or the USB (yes, I changed the boot settings from the BIOS), so I had the terrible idea of installing ubuntu from windows on the other partition and then boot with ubuntu and format the partition where windows was..... When I turned on the pc again I had a message about a file called NFSLT or something like that (sorry for my lack of knowledge XD) and when I try to install again ubuntu I get that F*cking message....


Can somebody please help me out?! :(

---

### Post by swapnilnarendra on 2011-03-03
I am sorry but DID you format your windows partition or is your windows still working ?

I dont understand why your system wont boot Ubuntu via a CD/USB ?
I guess it could be a hardware issue.
Have you tried checking your boot order while your USB was plugged in ?
It should show the name of the USB brand (in most cases) and thats how we can know that its recognizing your USB.

I had the same problem once but after my computer totally crashed it picked up my USB drive (my CD drive was totally wasted) and I have been using only Ubuntu since.

---

### Post by jose1522 on 2011-03-03
> **swapnilnarendra said:**
> I am sorry but DID you format your windows partition or is your windows still working ?

I dont understand why your system wont boot Ubuntu via a CD/USB ?
I guess it could be a hardware issue.
Have you tried checking your boot order while your USB was plugged in ?
It should show the name of the USB brand (in most cases) and thats how we can know that its recognizing your USB.

I had the same problem once but after my computer totally crashed it picked up my USB drive (my CD drive was totally wasted) and I have been using only Ubuntu since.


yes, I removed windows completely and also changed the boot priority, but when I'm installing ubuntu it freezes and won't go beyond the "loading" screen.... :S

---

### Post by mörgæs on 2011-03-03
It sounds like you need to add boot options:

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I guess that you are installing 10.10. You could also try 10.04.

---

