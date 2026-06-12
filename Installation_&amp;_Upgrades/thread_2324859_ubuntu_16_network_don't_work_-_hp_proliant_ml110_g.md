---
title: "ubuntu 16 network don't work - hp proliant ml110 g7 (gen7)"
date: 2016-05-17
forum: Installation &amp; Upgrades
---

### Post by cristiano9 on 2016-05-17
I have a HP Proliant ML110 G7 (Gen7) and the network don't work with Ubuntu 16.04 LTS server.
Ubuntu 14.04 LTS server works normally. But when I make new install of Ubuntu 16 the network card is founded but the DHCP and also fixed IP don't work.
Any help?

---

### Post by mastablasta on 2016-05-17
that's odd. it's using Intel 82574L Gigabit Network Connection so drivers are in kernel. did you check for any bugs in kernel regarding this driver? are there any error messages in logs (dmesg for example?!) that would indicate any error when loading the drivers?

I would say stay on 14.04 if it works and wait for the point release (if you must upgrade now). 

the server is certified for 12.04 anyway. but it should probably still work on 16.04.

---

### Post by cristiano9 on 2016-05-17
"[COLOR=#000000]check for any bugs in kernel regarding this driver? are there any error messages in logs (dmesg for example?!) [/COLOR]"
how could I do that?

please, look the image attached... configs seems OK but no network.

---

### Post by cristiano9 on 2016-05-17
I got the picture.

This HP server has 2 network ports. The "eno1" is the port number 2 and works normally.

BUT where is the port number 1? And how could I get it working?

---

### Post by cristiano9 on 2016-05-17
the network port number 1 has the ILO Shared Network Port also...

---

### Post by cristiano9 on 2016-05-17
I defined the enp2s0 network and plug the cable to the port number 1 and all seems to work right.
The big question is... why the enp2s0 name?! should it be called eno1 or eno2, shouldn't? Old Ubuntu it was em1 and em2

---

