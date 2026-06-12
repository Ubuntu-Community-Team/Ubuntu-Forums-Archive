---
title: "Intel Pro/100 VE not talking"
date: 2004-12-07
forum: Installation &amp; Upgrades
---

### Post by phr0s7y on 2004-12-07
Hello all,
I have dual booted a Toshiba 4600 notebook with Windoze. After installing Ubuntu I can't seem to get my nic to work.

I can assign IP, gateway etc manually and ping the local interface but ifconfig shows no packets in either direction. 
lspci reports "Ethernet Contoller: Intel Corp. 82801BA ............ (rev 03)
lsmod reports both e100 & eepro100 as loaded.

I have tried to do a rmmod and then and insmod on both modules then bring eth0 up but still no packets.

The nic works fine under windoze.

I've goggled around to try and find what  I am missing but most links just say the nic works from the start without problems.

Any ideas? Thanks.

---

### Post by gmc on 2005-07-09
Hmm, I just got home with my Toshiba Satellite Pro 4600 and am having the same problem. On the initial boot of the CD, the system recognizes and gets an ip address from my router (via dhcp). Then after installing grub and rebooting, it failes to see the router and get an ip address. No amount of rmmod/modprobing seems to help, though the system does load the e100 module automatically. 

G

*** UPDATE 10/July/05 ***

Success! Seems this laptop had never been maintained with updates. It was using the original v1.60 version of TBIOS. I downloaded v2.60 from Toshiba's website, installed it and did a complete re-install of Ubuntu. The built in network card is working fine now with the e100 module.

G

---

