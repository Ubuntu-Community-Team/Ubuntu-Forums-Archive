---
title: "Error message before install even starts"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by Dracosama on 2005-07-05
Ok I keep getting this error whenever I use the boot cd I made to try and install...

The system memory manage (EM386.EXE) has detected an error caused by a fault in one of the device drivers or programs loaded in the system.

Due to this fault the system is probably in an unstable state and you are therefore recommended to reboot the computer immediately.  If the problem persists, then try to isolate which program is at fault, (if you have loaded several, then load them one at a time until the fault appears) then contact the tech suport department for that program.

Advanced Tech Info
Exception 6 (Invalid Opcode).

This error code is then followed by a bunch of things that look like
Vs=02cb ES=1073 EAX=001210ca ect ect. 

Just making sure I am not being stupid my processor is a 64 bit 2.8 so that would mean I use the 64 version right?

Thanks.

Jeff

---

### Post by C.B. on 2005-07-05
[QUOTE=Dracosama]Ok I keep getting this error whenever I use the boot cd I made to try and install...
"...If the problem persists, then try to isolate which program is at fault..."
This error code is then followed by a bunch of things that look like
Vs=02cb ES=1073 EAX=001210ca ect ect. 
[/QUOTE]

Did you double-check to see that you downloaded the correct Ubuntu ISO installation file and that it copied correctly onto the CD as an **_ISO_** image. 

If that might be your problem, go to [www.ubuntulinux.org/wiki/BurningIsoHowto](www.ubuntulinux.org/wiki/BurningIsoHowto) . Scroll down to "Burning/writing an .iso Image to CD with Windows XP." There you will find out there is a missing component in the XP file transfer/CD burner thingy which you'll need to download and patch. Instructions are pretty straightforward. You can also get the CheckSum utility to verify that all files are intact (i.e., they were transfered correctly). 

This sounds like a pain, but if you haven't done it yet this could help solve your problem . . . or at least eliminate some of the possibilities. You pretty much have to do what your error message says: "try to isolate the fault." It took me a couple of downloads and at least 2 transfers to the CD before it came out right. Even after I got a good transfer and burn, if I remember right, I still got and odd error message or two when installing. At that point, because i was pretty certain the CD was okay, I just rebooted and and it installed without further problems. Sometimes sheer persistence seems to help. But *get all your ducks lined up* (CheckSum etc.) first.

I am new at this too, so I can't help you out much beyond that. If there's something more hopefully someone else can jump in with further advice.

---

### Post by Dracosama on 2005-07-05
Thank you I will give it a shot.

Jeff

---

