---
title: "Problems installing/upgrading to 6.06 and 6.10"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by samuel_k on 2006-11-11
Hi, I am quite new to ubuntu and I have troubles installing 6.06 and 6.10.

I have tried to install both ubuntu 6.06 and ubuntu 6.10 from alternate i386 CDs and desktop i386 CDs. 

With desktop CDs I can't even get to install ubuntu. The system just freezes.

With alternate CDs either of them (6.06 nor 6.10) could not detect my hardware: network device and hard drives. I get a list of hard drive drivers, but none of them works. I have three SATAII hard drives in my PC and windows xp installed to one of them and I am the meaning is to get ubuntu to work on one of them.

5.10 installs without problems and it works, so I tried upgrading 5.10 to 6.06 using guides found from the forums. The upgrading seems to go without problems, but when I restart and try to boot the newly installed kernel 2.6.15-27-386 I get error messages and I can't get any further.

   PCI: Error while updating region 0000:00:06.0/4
   PCI: Failed to allocate I/O resources...
   PCI: Failed to allocate mem resources...
   ...
   and finally I get the line 
   /bin/sh: can't access tty; job control turned off

I can boot the older kernel in the GRUB list. I tracked 0000:00:06 from the device manager in ubuntu and it points to CK804.

I have Asus K8N4-E Deluxe motherboard and I have Sempron 3100+ processor.
My video card is Sapphire RADEON X700 PRO and to get the Xserver work I have to use fglrx.

I would appreciate if someone could help me out and point me to right direction. As I mentioned in the begining I am new to ubuntu so I wish the support given is understandable and simple as possible so I can get this work. Thanks.

---

