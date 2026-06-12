---
title: "Booting Installer  on old computer"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by befused on 2006-11-25
I got a Procomm CS28P3 cheap at an auction.  I want to install a samba server on it.
the Motherboard is an Intel Marl:
pentium 200
80 meg ram, 1.2 & 1.8 gig hard drivex
Triton II chipset 
power supplies are switched through mobo<<ISSUE 1!!
BIOS does not support cdrom<ISSUE 2!!
   To find out if everything worked, I plugged the scsi cards into another mobo, installed Kubuntu there, and all the drives showed up  readable on the network.  Until the hard drive attached to that mobo started making noises like a cricket and nothing else. 
   I decided to go with the old mobo because of Issue 1.  I tried to use Tomsrtbt, but am to much of a unix newbee to get any results there. Sbootmgr abends with error 00AA.  
   I installed windows98 as a bootmanager.  I intend to install the server in its place.  Kubuntu 6.0.6 desktop is not showing me an install server selection. Ubuntu 6.10-server won't wakeup at all.
   I need a method of installing a server on the hard drive.  Hopefully through cdrom booting from win98, because network boot sounds like it would involve a lot of Visene & Advil (never done it).

---

### Post by confused57 on 2006-11-25
You can use the alternate cd to install a server.

When I use Smart Boot Manager, after selecting boot to cd rom, I have to press "enter" three times(ignore the error message).

---

### Post by befused on 2006-11-28
Thanks for the suggestion, but smart boot manager just doesnt work with this motherboard. If I press Enter many times, I see "Disk error!  0xAA" many times.

---

