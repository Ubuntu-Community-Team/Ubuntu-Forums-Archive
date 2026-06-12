---
title: "Ubuntu won't install - IDENTIFY PACKET DEVICE"
date: 2016-08-27
forum: Installation &amp; Upgrades
---

### Post by euanfoster on 2016-08-27
Hey all,

I built a PC a few years back with the following hardware:[INDENT]MotherBoard:Asus M5A99FX PRO
Processor: AMDFX8350
Graphics Card: Sapphire AMD R9270x
Ram: 16 Gb DDR3 1600 MHz
[/INDENT]

I have been trying for a while on and off to install ubuntu froma USB flash drive on my PC and I am having difficulty. 

When I boot into the flash drive, I can use the 'try and install ubuntu' option and it boots in and allows me to install. However, when I go to boot in from the hard drive it is installed on, it fails to boot. 

Also if I try and install ubuntu from the flash drive and select just the 'install ubuntu' option without trying it fails to even allow me to do this. 

Both times I get the following error message:
[PHP]
ata7.00: exception Emask 0x52 Sact 0x0 SErr 0xffffffff action 0xe frozen
ata7: SError: { blah blah }
ata7.00: failed command: IDENTIFY PACKET DEVICE
ata7.00: cmd blah blah
         res blah blah (ATA bus error)
ata7.00: status: { DRDY }
ata7: hard resetting link
[/PHP]

I have tried installing many different distros, ubuntu 12.04 14.04 and 16.04. Anyone got any ideas on what I can do to get this working?

---

