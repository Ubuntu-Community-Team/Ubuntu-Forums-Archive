---
title: "xorg.conf of ati radeon mobility x2300 ibex"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by barath on 2008-11-15
Hi,

I have a x86_64  kubuntu ibex installed , my present xorg.conf for mobility radeon x2300 looks like this

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
DefaultDepth 24
EndSection

Section "Module"
Load "glx"
EndSection

Section "Device"
Identifier "Configured Video Device"
Driver "fglrx"
EndSection


what should i add in this so that i can install compiz fusion.
And I installed the driver using the option install hardware drivers and activate the driver...
now i find that it says that my card is in use...

one more when i open catalyst for information i see the stuff in the attachment
but catalyst in vista shows hypermemory instead of the actual ram in the card do i need to edit something to get the full potential of the GPU..
Thank you in advance ..

---

