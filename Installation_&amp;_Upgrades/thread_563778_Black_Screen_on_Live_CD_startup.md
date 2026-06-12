---
title: "Black Screen on Live CD startup"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by Alien56 on 2007-09-30
I downloaded 4 isos from 4 different locations and always get the same problem. When I start the live CD and select to install it goes through several lines of white text and then when it looks like it's going to continue I get a black screen and it just hangs there. Is there anything I can do to fix this? My laptop has 512mb of ram so I don't see what the problem is.

---

### Post by Pumalite on 2007-09-30
Post all your specs, particularly video. You look like a candidate to the Alternate CD due to graphics issues or have a bad burn, or didn't burn as Image instead of data.

---

### Post by Alien56 on 2007-09-30
Alright first I did burn as an image and not data. I burned the iso that I downloaded with MagicISO. Second here are some of  my computer specs that are probably only worth knowing:

Graphics: nVidia GeForce Go 7200 (256mb)
Ram: 512 mb (DDR2-667 DDR2 SDRAM)
CPU: Mobile AMD Sempron 1800 MHz (1.8 GHz)

Let me know if you need other specs and please specify which ones. Thanks.

---

### Post by cowkiller on 2007-09-30
I had a similar problem with my laptop...there was any way possible to start the livecd. Maybe it's some problem with your graphic card. 
Finally I could install ubuntu in text mode from the alternate cd ([x86 version]("http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-i386.iso"), [64-bit version]("http://releases.ubuntu.com/7.04/ubuntu-7.04-alternate-amd64.iso")) , and after it, modify the /etc/X11/xorg.conf file to set "mesa" as the default graphic driver. After it you will be able to install your graphic drivers from the desktop. 
Good luck!

---

### Post by Pumalite on 2007-09-30
You r hardware is good to boot a Live CD. Follow the following guidelines:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Try the CD's in another computer,etc.

---

### Post by Alien56 on 2007-09-30
Hey,

I saw you post a link for installation on the HP dv6000 laptops, which Im going to follow. I have that one. Im downloading the alternate CD right now and I'll see how that goes.

Thanks.

---

### Post by Pumalite on 2007-09-30
Good. That's a good link. Good luck.

---

