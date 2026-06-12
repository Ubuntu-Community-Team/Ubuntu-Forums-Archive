---
title: "Ubuntu ATI driver crash!"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by Auctionedllama@gmail.com on 2008-04-16
Hi, I am running Ubuntu Studio and just finally got it up and running last night. I installed the ATI video drivers, and after restarting, much to my dismay, I got a blank screen! I can't ctrl+alt+f1 into  a terminal and am forced to restart. IF it helps any I installed the drivers that it said to, in the administrator options. Any help would be fantastic. Thanks!

---

### Post by Auctionedllama@gmail.com on 2008-04-16
Bump

---

### Post by Auctionedllama@gmail.com on 2008-04-16
Sigh.. Bump.. again. Also I have an ATI Radeon X1650..

---

### Post by Saint Angeles on 2008-04-16
i could not get any version of fglrx to work with the realtime kernel.

thats why i went back to regular ubuntu with the generic kernel.

---

### Post by overdrank on 2008-04-16
> **Auctionedllama@gmail.com said:**
> Sigh.. Bump.. again. Also I have an ATI Radeon X1650..

HI and please do not bump that quickly, have you tried and  reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` by using the ctrl, atl, F1 keys you mentioned. Then use the command ```
reboot
``` hopefully this will get you to a GUI, Desktop. Then you may also try Envy if you are still having troubles with the drivers 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
 Good luck.

---

### Post by Auctionedllama@gmail.com on 2008-04-16
Well I tried "sudo dpkg-reconfigure xserver-xorg" and when I switched drivers to ATI it didn't work but vesa or w/e it is did. I will try the other command see how it turns out. And sorry bout the bumping.

---

### Post by Auctionedllama@gmail.com on 2008-04-16
OK, thanks, I went ahead and tried envy, and got my card working and the right resolution going. Thanks a ton. But now when I try to enable any effects/compiz I get a white screen. Is there a fix for this?

---

### Post by Auctionedllama@gmail.com on 2008-04-16
Bumpity Bump bump

---

### Post by Auctionedllama@gmail.com on 2008-04-16
bump.. again

---

