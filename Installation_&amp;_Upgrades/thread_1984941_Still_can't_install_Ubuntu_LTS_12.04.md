---
title: "Still can't install Ubuntu LTS 12.04"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by Enkindlers on 2012-05-22
Hi! I am new to Ubuntu and I am still discovering settings and ubuntu potential but sometimes I've made big mistakes that require reinstall. 

This thing is not possible now with UBUNTU 12.04 because I can't install it. It only works if I upgrade from 11.10 to 12.04 but the process take longer than a fresh install.

In other words: the installation starts from USB and when it came to the "welcome" screen (where is supposed to choose language) the mouse pointer moves very slowly, it basically responds after few seconds and the "continue" button can't be pressed.  I have waited half hour and nothing happens. 

If anyone had this problem and solved it please help!

---

### Post by zvacet on 2012-05-23
You can try install with alternate CD.You can find screenshots [here.]("http://members.iinet.net.au/~herman546/p2.html")

---

### Post by Maro848 on 2012-05-23
I have seen this issue with a couple of machines with low amounts of ram in those situations I do as is recommended above and install from an alternate install cd iso image instead of the live cd you would normally download.

---

### Post by jadtech on 2012-05-23
here is another trick that might work  if you have windows installed and working  .. 

pop on windows  down load Gparted  for window if you have already  shrank the volume of window to makew room for unbuntu  go to gparted  and make a 2gb swap partition when you try to boot  the live cd it will mount swap automatically and speed things up big time ..

---

### Post by Enkindlers on 2012-05-25
Well, I have tried to install alternate and I had an error during installation. Never tried again, but i will.

I have 4GB RAM and I don't think this is the problem.

Ubuntu is installed on a separate HDD and no other OS is installed on my PC.

---

### Post by fantab on 2012-05-25
Boot with your 12.04 LiveCD and don't install directly, use "Try Ubuntu"... let the live cd boot. Play around and get your internet connection going.

After a while, Install Ubuntu from desktop or launcher. (I had trouble installing 12.04 on my bro's PC and the said workaround worked).

Desktops/Laptops with more than 2gb Memory rarely use SWAP, however I have found that we cannot not have it... however small (512mb) but keep it. If you have windows do as post #4 recommends or use [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") and use it from partition at boot.

---

### Post by xXQuadPolarXx on 2012-05-25
> **fantab said:**
> Boot with your 12.04 LiveCD and don't install directly, use "Try Ubuntu"... let the live cd boot. Play around and get your internet connection going.

After a while, Install Ubuntu from desktop or launcher. (I had trouble installing 12.04 on my bro's PC and the said workaround worked).

Desktops/Laptops with more than 2gb Memory rarely use SWAP, however I have found that we cannot not have it... however small (512mb) but keep it. If you have windows do as post #4 recommends or use [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php") and use it from partition at boot.

I agree I have a lot of problems getting it to install if I don't do as stated above. I always lets the CD/DVD load up in the Try mode then after a bit I will use the Install Ubuntu option from the desktop. As for the USB booting I don't bother with that anymore as none of them have worked right for me after 7.04

---

