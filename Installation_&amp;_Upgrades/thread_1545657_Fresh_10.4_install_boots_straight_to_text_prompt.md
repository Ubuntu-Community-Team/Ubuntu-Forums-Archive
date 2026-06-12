---
title: "Fresh 10.4 install boots straight to text prompt"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by kurry on 2010-08-04
Whenever I choose ubuntu on grub it'll function perfectly, but boot into a text login rather than a graphical one. I don't see a splash of any kind, just a blinking cursor and then the standard text login. 

I tried using 
```
sudo /etc/init.d/gdm start
```
but this just spat out some error at me, and eventually instigated a low-graphics mode. In that mode the display would never actually restart, and it'd just freeze on that screen until I pressed okay and then it went back to the prompt. 

I found out however if I use startx everything boots fine, but I either cannot (or can't figure out) how to mount any of my external hard-drives, nor get my usb wireless adapter to work for an internet connection, the network manager icon doesn't show. 

Any ideas?

---

### Post by corrytonapple on 2010-08-04
Did you do a bare installation? You are using 10.04 I assume and not 10.4. 10.4 is in beta. Do you have an add on card?

---

