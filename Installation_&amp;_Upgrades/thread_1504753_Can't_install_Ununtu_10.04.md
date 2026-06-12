---
title: "Can't install Ununtu 10.04"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by MaxTesla on 2010-06-08
Can't install Ununtu 10.04
 
 
I can not install ubuntu 10.04 32 or 64 bit on my computer
 
 
Every time I put in either DVD I get a guy and next to him is a regtangeler box, then the screen goes black with a blinking white line up to the left and then it goes completely black then monitor turns itself off
 
 
This happens with both 32 and 64 install versions
 
 
So how do I install it or just use it a s a live cd
 
 
I have a pretty new computer that I Run windows 7 on that I am trying to get Ubuntu on
 
 
System Manufacturer: FUJITSU 
 
System Model: ESPRIMO P1500 
 
BIOS: Version 6.00 R1.05.2950.A1
 
 
Processor: Intel(R) Core(TM)2 Quad CPU Q8300 @ 2.50GHz (4 CPUs), ~2.5GHz
 
 
Memory: 4096MB RAM
 
 
Available OS Memory: 4094MB RAM
 
 
Page File: 1249MB used, 6937MB available
 
 
Windows Dir: [C:\Windows]("file:///C:/Windows")
 
 
DirectX Version: DirectX 11
 
 
DX Setup Parameters: Not found
 
 
User DPI Setting: Using System DPI
 
 
System DPI Setting: 96 DPI (100 percent)
 
 
Card name: NVIDIA GeForce GT 220 
 
 
Manufacturer: NVIDIA
 
 
Chip type: GeForce GT 220
 
 
DAC type: Integrated RAMDAC
 
 
 
 
Help me

---

### Post by ronparent on 2010-06-08
Hit space when the guy and the box come up. This should present you with a menu. At this point hit f6 which allows you to select boot parameters, You probably ought to select momodeset 1st. Then erase **quiet splash** from the boot line which came up when you hit f6. This will allow the boot messages to scroll the screen and give some hint as to what may be preventing the boot to complete. Post what you experience so someone can give you additional advise. Good luck.

---

### Post by MaxTesla on 2010-06-08
Ok I did that


I got lots of lines, but the one that stuck out was


BUG CPU#1 stuck for 61 seconds! Mode 344

---

### Post by ronparent on 2010-06-08
What were the last 6 or so lines that printed?

---

### Post by MaxTesla on 2010-06-08
I have no clue some strange lines to me
 
Are you asking me to copy them down by hand
 
Then I must ask you before I do that, will that with 100% certainty fix my problem?

---

### Post by ronparent on 2010-06-08
There is no 100% certainty. The type problem you have posted indicates an exception somewhere in your system that wasn't handled in crafting the boot routines or picked up in a prior bug report. The problem is now to try to pin it down to find a hopefully easy work-around (most often among the f6 choices). Can you post a picture of the script endpoint (maybe with a digital camera)?

---

### Post by bquietndrive on 2010-06-08
i got a problem  with the ubuntu boot cd i restart the pc, run from cd then a bit after  appears a error message "Installation Failed" " The installer  encountered an unrecoverable error. a desktop session will now be run so  that you may investigate the problem or try installing again." i burned  over 5 cd's at various speeds an always appears this message i try to  install by entering the live cd but it doesn't install. can anyone help  please.

Thanks.

---

### Post by MaxTesla on 2010-06-08
> **ronparent said:**
> There is no 100% certainty. The type problem you have posted indicates an exception somewhere in your system that wasn't handled in crafting the boot routines or picked up in a prior bug report. The problem is now to try to pin it down to find a hopefully easy work-around (most often among the f6 choices). Can you post a picture of the script endpoint (maybe with a digital camera)?
 
 
No digital camera sorry
 
Maybe I will just wait for the next version to come out maybe that version will work
 
But on a side note I have the last version version 9.10 on a dvd and it was the 32 bit version and that version did not work as well, but both the old 32 bit 9.10 and this new 10.04 32 bit works on my laptop which is way older than my stationary computer

---

