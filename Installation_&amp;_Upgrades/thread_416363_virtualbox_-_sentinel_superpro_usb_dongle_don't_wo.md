---
title: "virtualbox - sentinel superpro usb dongle don't work"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by zub on 2007-04-21
Hi,

I was not successful using vmware 5.5.2 in order to install an application requiering a usb-dongle to run (sentinel superpro), so I switch to virtualbox. 

Unfortunately, I have the same problem with virtualbox. Here is my problem: 

host: ubuntu on a ix86 32 bit architecture with everything working fine out of the box;
guest: WinXP pro with SP1

Virtualbox installed and WinXP installed as guest. 
The usb dongle has been recognized in Linux and I added it to Virtualbox without difficulty. 
I start XP and it recognizes the usb dongle and wants to install it; after several tryings (reboot, reboot), WinXP always fails to install the sentinel driver for the dongle (it seems to do it, but it finally ends up with an issue, the usb-controler becoming the usual yellow flag with the 'warning' (!) sign). I downloaded the last driver from the sentinel web pages, but same result. 

It is the only one application I need to bring at work with XP (no success with wine), and it would be a pain to do a fresh XP install just in order to be able to use this soft (which I have to use). So, if someone could help me, it would be just great!

yours

PS: just to satisfy my curiosity - how much usb peripherals does Vbox support? it seems that vmware supports only 2
zub

---

### Post by misha680 on 2007-05-04
Btw, I run VMWare (free) Server (latest version) with WinXP and was able to use the SuperPro Dongle just fine with it (I do remember sometimes I had some weird USB problems wiht a different USB device and had to reboot the computer with it plugged in at startup before VMWare would recognize it, but I think this is due to having VMWare auto-boot XP at bootup).

MIsha

---

