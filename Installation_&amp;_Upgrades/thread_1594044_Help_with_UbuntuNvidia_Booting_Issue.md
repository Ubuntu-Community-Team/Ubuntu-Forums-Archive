---
title: "Help with Ubuntu/Nvidia Booting Issue"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by nfishbone on 2010-10-11
Hey everyone I'm pretty new to ubuntu/linux so please bear with me :). I recently installed 10.10 on my new htpc. The initial install went great, until I went to install the updated driver for my graphics card. What I did was I downloaded the driver off of nvidia. Then I did these steps: 
1. ctrl-alt-f1  
2. logged in 
3. sudo services gdm stop
4. I then located the driver package that I downloaded and ran it, it seemed to install fine (except for an error about some install script? but it let me proceed)
5. sudo services gdm start

It went to the gdm/ubuntu desktop. However I then connected it via HDMI, and the resolution was way off (top bar was not even displayed on TV) and I tried many different settings but no luck in fixing it. Next after restarting it did not automatically boot to the gdm/desktop. Instead it stayed at the command line login (the ctrl-alt-f1 screen).

tl;dr : 1. How to make it automatically boot to the gdm/desktop after I updated my gpu driver
2. How to fix the resolution for HDMI from my gpu to my TV. (DVI works fine)

Thanks!

---

### Post by stee1rat on 2010-10-12
Just wonder - why didn't you update it through System - Administration - Additional Drivers?

---

