---
title: "graphics card update?/ cable box"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by krammerak on 2010-01-30
Here is what I have:
$ lspci

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

I am running ubuntu and windows 7 on this desktop (that I have had for a while).  I dont think the ubuntu is taking advantage of the graphics card.  When I go to change the visual effects I can only be set to None because when i try to set it to Normal or Extra it says "could not be enabled."
The exact number Is Radeon 9250.  I was able to find the windows 7 driver and got it to work on there.  But I'd like it to work on ubuntu as well.  Any suggestions?


Also, on a side note I have a TV tuner on this desktop,  Couldn't find the drivers for it on windows 7, was wondering If i could still take advantage of this? It came from evga.com    -

> "
Driver Version :                      1.20.45 - EVGA  Recommended Download                                                                                
 Release Date:                       02/02/2005                                                                    
WHQL Certified :                          YES                                                                                
Driver File :                     NVTV.exe  ([Primary Download Link]("ftp://ftp.evga.com/Driver/NVTV.exe"))                                                                                             
Notes :                            THIS DRIVER FOR USE WITH MICROSOFT  MEDIA CENTER EDITION 2005 ONLY
 
[LIST]
[*]This  is the same version shipped on the driver CD
[*]This  driver does not include the DVD CODEC, which must be  acquired separately
[/LIST]
"

I originally had Windows Media Center on this computer

---

### Post by Mark Phelps on 2010-02-01
There is no ATI Linux driver for your card that works with Ubuntu versions newer than 8.10.  

Your card is detected automatically during Ubuntu installation and the proper open source drivers are installed automatically.  IF you're seeing a graphical desktop, you already have them installed.

There is no updated Linux driver that you can install.

As for the Windows 7 question, your best bet would be to go to the Windows 7 forums for answers. Check out sevenforums.com.

---

