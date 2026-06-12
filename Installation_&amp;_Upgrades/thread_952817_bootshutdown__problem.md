---
title: "boot/shutdown  problem"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by pratikkaushik on 2008-10-19
Hi, I am very new to linux, i tried installing ubuntu 8.04.1 LTS, using official CD from Canonical Ltd.
But when i tried it the screen goes grey, and it keeps fading too, and no message is visible on the screen.
Next time i tried to boot ubuntu in safe graphics mode and it booted with minor display problem, it works great there but again when i shutdown my system, the screen again started fading down. 
Everytime it acts like that, please help me to resolve my problem i want to install Ubuntu on my laptop.

Details of my laptop are :
Intel Dual Core, T2330 processor, 1.60 GHz
1 GB RAM, 
VIA Chrome9 Chipset with inbuilt graphic card.
WLAN, DVD Writer, etc.

Please help me.

Thanks

---

### Post by Shazaam on 2008-10-19
A quick and dirty way to shutdown the livecd is to open terminal (Applications>Accessories>Terminal) and enter either ...
```
sudo reboot
```
or...
```
sudo shutdown -h now
```
(this tells Ubuntu to shutdown, then halt, now)

More than likely your video chipset is the problem. I have zero experience with Via Chrome drivers so you might try some searching here on the forums or an advanced search with google.

---

### Post by aashay on 2008-10-19
Assuming you have a LCD monitor, the problem is related to usplash. I've not used the install cd for quite some time, but you need to remove the 'splash' from the kernel parameters when it boot. I'm sorry i can't give you specific instructions to do so. I think it will require you to press F2 or TAB - just look around on the screen - to enter the 'advanced options'. You will hopefully be presented with a long string with the words 'quiet' and 'splash' in it. Remove these words. All this is to be done with the default selection highlighted in the very first menu you see (where you selected the safe gfx mode)
Even if you can't make sense of what I've posted, waiting 12-15 mins should boot the livecd up. You just wont be able to see the pretty progress bar.

---

