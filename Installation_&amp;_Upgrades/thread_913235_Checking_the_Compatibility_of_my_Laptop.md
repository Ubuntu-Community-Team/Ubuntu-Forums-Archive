---
title: "Checking the Compatibility of my Laptop"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by monsieurdozier on 2008-09-07
I don't like Windows Vista, but I just bought a new laptop, and it came preinstalled.

I bought a Toshiba Satellite L305-S5875 from Best Buy.

I'm not so much asking everyone to tell me if my computer is compatible or not, but where on the internet can I go to find out if it is compatible.

-Monsieurdozier

---

### Post by Partyboi2 on 2008-09-08
[https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba](https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba)
I don't know how up to date that page is. If you don't find your laptop listed on that page it does not mean that it is not compatible. Just means you might need to pioneer the way :razz:

---

### Post by wzhang on 2008-10-18
I bought a Toshiba L305-S5908 with 64-bit Vista Home pre-installed.
Processor & Memory:
    * Intel® Core™ 2 Duo Processor T5800 (2.0GHz)
    * 4GB DDR2 SDRAM memory
Drives:
    * 320GB (5,400 RPM) SATA hard drive
Graphics & Video:
    * 15.4" widescreen TruBrite TFT LCD display; 1280 x 800 (WXGA) native resolution
    * Mobile Intel Graphics Media Accelerator 4500MHD (shared)

I have tried to install Ubuntu 8.04 64-bit AMD64 and I could run Ubuntu command-line only version of Ubuntu but GNOME or the X-window system does not work on this laptop. 
Does this mean the video card on this laptop is not supported by Ubuntu?
I have tried the following
1. install 32-bit Ubuntu (got the installation menu but after that the screen went to blank or mixed colors)
2. install 64-bit from 8.04 live-CD (tried setting different boot options such as vga=771, same display problem)
3. install 64-bit from 8.04 alternate CD (managed to install everything from text mode successfully but after rebooting, I cold not even see the login screen, I can hear the greeting sound though)
My goal is to use this laptop for dual boot (Vista and Ubuntu),
but from what I have experienced, it seems Ubuntu does not support the video card. 
Or Is there anything I can set to make the display work for Ubuntu?    Thanks, 
-Wayne

---

### Post by mikewhatever on 2008-10-18
Having been launched in June 2008, Intel Graphics Media Accelerator 4500 in too new for Hardy. [http://en.wikipedia.org/wiki/Intel_GMA#GMA_X4500](http://en.wikipedia.org/wiki/Intel_GMA#GMA_X4500)
You may want to try the upcoming 8.10 version instead.

---

### Post by wzhang on 2008-10-18
Well,  Mikewhatever,  you are exactly right!  
Thank you! (I am new to the forum, how do I add a "Thank you" to your account?

I tried 8.10 beta and the gnome works fine!  I will try  few other things tomorrow.

monsieurdozier, before you buy the laptop, you need to check what kind of video card and perhaps a few other things in the machine.  If it has the same video card as what's in my machine, any Ubuntu older than 8:10 may not work on the machine.

---

### Post by kfaidzah on 2008-11-03
i've installed ubuntu 8.10 in my machine )vaio VGN SR12G) which is using Mobile Intel® Graphics Media Accelerator 4500MHD for the graphic. However i couldnt get the right resolution to my laptop... the highest i can get is 800X600.. 
can some1 help me to get a higher display setting...

---

