---
title: "Instal and Using Avermedia EZmaker PCI Deluxe"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by domentarion on 2008-04-15
Hello, 
 
For my work i have to install the Avermedia EZmaker PCI Deluxe on a ubuntu or kubuntu server. I think i have installed the drivers correctly, because when i do dmesg | grep ivtv i get :
 
[ 11.360000] ivtv: Start initialization, version 1.2.0
[ 11.360000] ivtv0: Initializing card #0
[ 11.360000] ivtv0: Autodetected AVerMedia EZMaker PCI Deluxe card (cx23416 based)
[ 11.360000] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[ 11.400000] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[ 11.400000] wm8739 0-001a: chip found @ 0x34 (ivtv i2c driver #0)
[ 11.408000] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[ 11.408000] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[ 11.408000] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[ 11.408000] ivtv0: Registered device video24 for encoder PCM (320 kB)
[ 11.408000] ivtv0: Initialized card #0: AVerMedia EZMaker PCI Deluxe
[ 11.408000] ivtv: End initialization
[ 54.652000] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[ 54.852000] ivtv0: Encoder revision: 0x02060039
 
Now i try to test it with the command :
 
cat /dev/video0 and the after 10 seconds i wanne play it and the screen is black and it stays that way. 
 
I have check the cabled and i add another input device at the videocard. So i try vlc to open the device. I try it with the v4l driver and with the pvr but none of this would work.
 
Does somebody have a solution for this ? Or a suggestion ?
 
Greetz
 
Sander

---

