---
title: "ubuntu 7.10 64bit installation help"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by or1on on 2008-01-08
hi all, ive tried installing kubuntu 64 bit and debian etch64 bit and had basically the same problem, ive also posted this on the kubuntu forums but got no answer there as of yet. so im wanting to install ubuntu 64 bit now but afraid i will have the same problem, hopefully someone can tell me the commands to issue at boot when i install to avoid this...anyway the 64 bit installs fine tells me to take the cd out and reboot however after grub loads the last screen i see is kernel is alive mapping kernel 100000-8000 or something like this then the pc seems to go into a sleep mode or the video signal is killed at least and never comes back?any help is appreciated
my specs 

Foxconn C51XEM2AA- 8EKRS2H AM2 NVIDIA nForce 590 SLI 
AMD Athlon 64 X2 5600+ Windsor 2.8GHz
CORSAIR XMS2 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800
BFG Superclocked 8800GT 512mb
creative XFI extreme gamer sound card
segate 160gb sata drive

---

### Post by or1on on 2008-01-09
*bump*
anyone :)

---

### Post by spartus4 on 2008-01-09
I am having the same problem.  I hope someone has found a work around.

spartus4

---

### Post by or1on on 2008-01-09
i tried something a bud had told me in irc a few days ago and i was able to boot the 64bit ubuntu live cd by getting rid of quiet splash and adding nosplash noapic and nolapic to the boot command (no idea what the cmds do though :/ ) that brought me to a cmd prompt instead of the dreaded monitor turning off, then i was able to reconfigure the xserver to use the vesa driver and got x going so my question is now when i install this to my harddrive how do i permanently pass this on so it always boots like this? and if someone could maybe explain whats actually being turned off by issuing these commands thnx in advance :)

---

