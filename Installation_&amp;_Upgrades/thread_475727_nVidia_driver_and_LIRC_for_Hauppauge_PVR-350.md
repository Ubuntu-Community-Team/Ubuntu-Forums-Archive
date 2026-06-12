---
title: "nVidia driver and LIRC for Hauppauge PVR-350"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by drywhenwet on 2007-06-16
Hi.

Just recently I made my first step away from Windows and decided to install Ubuntu for my home PC.   I have encountered some problems but I was able to fix them through the forum.  However, I have problem with my  GeForce 8500 GT and Hauppauge PVR-350 capture card (particularly the IR receiver).

I have downloaded and installed the NVIDIA driver (version 100.14.09) since the one installed is relatively old.    I also compiled LIRC (0.8.2) following this guide [https://help.ubuntu.com/community/Install_Lirc_Feisty](https://help.ubuntu.com/community/Install_Lirc_Feisty) because using the installed LIRC does not seem to work for me.  After the compilation of LIRC my remote works well.  However, when I tried to reboot I can't start X.  Only to find out that my NVIDIA driver is missing. I installed the NVIDIA driver again and started X.  But this time my LIRC won't work without installing again.  However, doing so would end up error starting X after reboot.  So, I've been in circle for the past 4 days.

How can I compile LIRC without messing my NVIDIA driver?  Btw, here's what I got when I checked the status of modules selecting only "i2c" pattern
i2c_ec                  6016  1 sbs
lirc_i2c               11268  0
lirc_dev               15988  1 lirc_i2c
i2c_algo_bit            8712  3 cx88xx,bttv,ivtv
i2c_core               22656  12 i2c_ec,cx88xx,bttv,[COLOR="Red"]lirc_i2c[/COLOR],msp3400,saa7127,saa7115,tuner,ivtv,i2c_algo_bit,tveeprom,[COLOR="Red"]nvidia
[/COLOR]

I really appreciate any hints to fix this problem.  My progress on this really affects  WAF (Wife Acceptance Factor) :-( 

Best regards and thank you.

---

