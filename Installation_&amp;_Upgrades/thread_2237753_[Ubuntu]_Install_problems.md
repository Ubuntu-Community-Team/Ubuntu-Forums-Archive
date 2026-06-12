---
title: "[Ubuntu] Install problems"
date: 2014-08-03
forum: Installation &amp; Upgrades
---

### Post by robert117 on 2014-08-03
I don't want to keep Windows on this because I plan to use Wine. I'm just trying to put Ubuntu on it.
  
Specs:
  
-  M5 a99FX Pro R2.0 motherboard
-  AMD FX(tm)-8350 Eight-Core Processor
-  16 GB memory
-  64 bit processor
-  GTX660-DC2 Series NVIDIA
-  Two DVD/CD-ROMS drives
-  They are: ATAPI iHBS212 2 ATA and HL-DT-ST DVDRAM GH24NS90 ATA Device
-  Currently on Windows 8.1
  
I'll provide anymore information if it's necessary. I boot from my live CD that I don't believe is corrupted because the MD5 checks out.
  
I've tried typing these things and placing the little x next to them after the f6 popup comes up:
  
-  nomodeset
-  noquiet nosplash
-  acpi=off
-  nolapic
-  Changed OS type to other OS in the bios (I can’t disable secure boot state and I read this does the exact same thing)
-  Launch CSM in enabled and boot device control is set to legacy OpR
  
It either brings me to a black screen with a purple stripe on the very left side or to a black screen with a white input line blinking. I've also tried booting from a USB but that didn't work either. I've read a bunch of suggestions from Google search results but I don't want to keep making changes when I don't really know what I'm doing.


Here are pictures if I wasn't clear.  

**I've recently switched my bios to default**
  
I think [this is an album]([http://imgur.com/a/D03fm](http://imgur.com/a/D03fm)), but if that doesn't work, these are all the other pictures.
[Imgur]([http://i.imgur.com/djsGX0B](http://i.imgur.com/djsGX0B))  
[Imgur]([http://i.imgur.com/wkt7Y1I](http://i.imgur.com/wkt7Y1I))  
[Imgur]([http://i.imgur.com/lgHtSnI](http://i.imgur.com/lgHtSnI))  
[Imgur]([http://i.imgur.com/xOndONl](http://i.imgur.com/xOndONl))  
[Imgur]([http://i.imgur.com/oDVEZJ3](http://i.imgur.com/oDVEZJ3))  
[Imgur]([http://i.imgur.com/ILQyGMx](http://i.imgur.com/ILQyGMx))  
[Imgur]([http://i.imgur.com/uKNZIvt](http://i.imgur.com/uKNZIvt))  
[Imgur]([http://i.imgur.com/i3rjLPw](http://i.imgur.com/i3rjLPw))  
[Imgur]([http://i.imgur.com/HWGzxiX](http://i.imgur.com/HWGzxiX))  
[Imgur]([http://i.imgur.com/ojZpnHc](http://i.imgur.com/ojZpnHc))

---

### Post by Rob Sayer on 2014-08-04
I'm not an Nvidia expert ... never personally dealt with them ... but here's a promising looking link:

[http://askubuntu.com/questions/61396/installing-nvidia-drivers](http://askubuntu.com/questions/61396/installing-nvidia-drivers)

One more thing though:  Wine is NOT very reliable.  Intending to rely on it is a very common noob mistake which leads to grief.  And other similar programs like playonlinux are no better.  In fact playonlinux is just wine with a different GUI.

In other words, I highly recommend keeping at least one Windows partition.  Run it dual boot or boot linux and run Windows in a virtual machine like Openbox, which *is* reliable.

The best way to do dual boot if possible is to use 2 HDs, leave one with windows installed, and install ubuntu on the other one.  It's the most reliable way to do it.

---

### Post by Mark Phelps on 2014-08-04
> I don't want to keep Windows on this because I plan to use Wine. 

Don't know what you've been told, but Wine is not a replacement for Windows.  Some stuff works well in Wine, some not so well, and a lot, not at all.

You should go to the WineHQ website, their application compatibility tool, and look up the version of each Windows app you want to run.  Anything not listed, or rated less than Gold is not going to work well enough to be useful.

---

