---
title: "Ubuntu 10.10 64bit on Laptop Can't load window manager unless safe mode"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by Ali Akdurak on 2010-11-23
Hello everyone

I Installed on my laptop(Acer Aspire 8730) Ubuntu 10.10 amongst with Pardus 2009.2 and Windows 7 just to try and see the new Ubuntu and get accustomed to the gnome environment. Unfortunatly I can only login with safe session setting otherwise get an empty screen with just a mouse pointer. I assumed it was a windows manager problem so go into a terminal and tried several things which I found from the google like metacity -replace. It only responds as saying "Window manager error: Unable to open X display". 

I am a computer engineer and have a basic understanding but couldn't locate the error log files (sorry) Can anyone provide me with some guidance around this issue.

Aspire 8730 has an ATI (4100 series checked with sudo lshw -c video) graphic card(I know their Linux drivers suck). I cant get updates as I coulndt managed to get the ethernet nor wireless work in safe mode.

---

### Post by sikander3786 on 2010-11-23
Hi and Welcome to the forums :-)

Did you install the proprietary drivers for ATI?

fglrx seemed to cause a few problems in Maverick but not with your graphics card at least.

You can bring up the ethernet from terminal by using

```
dhclient eth0
```

Where eth0 is your network interface.

---

### Post by Ali Akdurak on 2010-11-26
I tried that and manage to get connected to internet and get the latest drivers (168 package updates or something.) But it didnt solve my Unable to open X Display problem 

&#304;s there a log file of Xserver where I can check the problem in detail or post it here ?

---

### Post by dino99 on 2010-11-26
10.10 use grub2 (grub-pc) and dont work well if it find grub (legacy) and menu.lst. Is pardus using grub2 or grub ?

first: safe mode issue

sudo grub-mkconfig
sudo update-grub


second: driver issue
you might need xserver-xorg-video installed (system admin synaptic) and activated (system admin additional driver)

---

