---
title: "Installation stops/crashes"
date: 2014-04-13
forum: Installation &amp; Upgrades
---

### Post by sven5 on 2014-04-13
Trying to install Ubuntu 12.04 from Live CD besides Win 7 x64 but installation stops/crashes before window wheather to install to hard disk or not. Included 2 pictures how installation ends. Most common is the scrambled "green" screen. Previously I tried to install some Fedora distro and the same scrambled screen. So, there must be something with the machine, probably in BIOS?

The computer:
Motherboard Gigabyte GA-X58-USB3
Processor Intel I7
Installed memory 16 gb
Graphics Nvidia GeForce GT 240
Windows 7 64bit

---

### Post by Double.J on 2014-04-13
Hi there! 

Welcome to the forums, sorry to hear about the situation. The scrambled screen suggests that it may be a graphics issue with your nvidea card. 

I suggest adding a boot parameter. 
At the boot menu, try pressing F6, followed by selecting 'nomodeset'
If you are unable to get an option popup by pressing F6, use the up/down arrows to select ubuntu, press the 'E' key on your keyboard. You'll see something like
```
linux /boot/image    Root=UUID=somenumbersandletters    ro quiet splash
```Try typing nomodeset between 'ro' and 'quiet splash'

let us no how you get on. 
It may be necessary to replace the driver also once the system loads, but we'll cross that bridge if we get there!

Jj

---

### Post by sven5 on 2014-04-14
The solution worked and I was able finally to install, thank you! But after restart the same scrambled screen appeared and I again inserted 'nomodeset to launch Ubuntu. The screen picture has definitely wrong resolution. You say that the driver must be replaced, so in my case, which one must I choose?

---

### Post by sven5 on 2014-04-14
Found drivers under Additional drivers and now Ubuntu starts with no complications. Thanks once more!

---

### Post by su:bhatta on 2014-04-14
Hi, glad you got that sorted out.

---

