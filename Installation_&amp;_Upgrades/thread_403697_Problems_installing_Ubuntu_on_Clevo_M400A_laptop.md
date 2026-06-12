---
title: "Problems installing Ubuntu on Clevo M400A laptop"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by CazH on 2007-04-07
Hi 

I have a Clevo M400A laptop which is a barebone system sold to many dealers who then put thier own label on it.

But anyway, I have some trouble getting it to run Ubuntu. I have tried just about everything by now. Breezy Dapper and Feisty. I have gotten the best results with the new Feisty Beta. Breezy I have tried netboot install, live cd, netinst cd and just a normal install cd, all of these I have got working on other computeres so it's not bad cd's or anything. With dapper I have tried both live cd and normal neither wants to boot. With Feisty I finally got something working, I burned out a netinst cd and got it up and running, the install detected both my wired NIC and my wifi NIC proberly and got det wired one confiugre with my dhcp server. After installing base system and kernel it starts to configure diffrent things, at this point the install freezes at 6% and there is nothing I can do.

Things I have gotten working on this laptop is Windows XP and Debian, but in Debian I just didn't want to get my 2 NICs up and running. I tried updating to kernel 2.6.20.14 that has the newest sk98lin driver that my wired NIC uses but it still won't dectet my wired NIC and I have also tried to update to newest version of the ipw2200 driver and as with the wired NIC this doesn't detect my wifi NIC.

I'm going crazy over this please help me, tell me what I'm doing wrong?

The computer:
Intel Centrino 1.8ghz (singel core)
2x512MB DDR2
Marvell Yukon PCI-E GBit NIC
Intel 2200BG Wifi NIC
Samsung 80gb
DVD-/+R/RW dual-layer
ATI X700 Mobilty

I'm not new to linux in generel I have 2-3 computers at all time running Debian or Ubuntu and have succesfull setup most things such as, printers networking, dhcp server, ftp server, ssh, apache, amule, nfts and a lot of other things. But this I just can't crack... HELP!

CazH

---

### Post by CazH on 2007-04-07
I forgot to say. That when install Debian I had to disable PC Card servics. And after install, boot in to safe mode and delete cardmgr. That was the only way to boot up the laptop without it freezing up on me.

CazH

---

