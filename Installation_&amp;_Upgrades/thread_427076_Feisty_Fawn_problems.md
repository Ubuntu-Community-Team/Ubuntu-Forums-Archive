---
title: "Feisty Fawn problems"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by plbuckland on 2007-04-29
I have an Asus A7CC laptop which I set up dual booting with Ubuntu 6.10 and Vista Home Premium. Via the Ubuntu upgrde manager I installed Feisty Fawn and all was going OK with the update until it started setting up wvdial (last 3% of the upgrade), when it crashed. When I go in via the recovery console I get the following error: 
[17179727.03200] serial8250: too much work for irq4
[17179727.32800] serial8250: too much work for irq4
[17179727.56400] serial8250: too much work for irq4

From reading other posts this error looks like it may be connected to the serial ports in the laptop. I have looked at the bios and there is nowhere in the bios that I can set the management of the serial ports. I have even downloaded and installed the latest bios update from Asus - no different. Bios is American Megatrends v02.59 version 205. There is nowhere in the bios I can set irq's or where serial ports are even listed, unlike older bios. I can no longer load either Ubuntu 6.10 or 7.04, and can only access the recovery console for 6.10 which is where I get the error listed above. Vista still boots OK so the problem is confined to Ubuntu FF. At the minimum I would accept being able to disable the serial ports (if that is the problem) until a fix is available. Currently Ubuntu is not available - only Vista.

---

### Post by plbuckland on 2007-05-04
Furthur to this problem, I downloaded the 7.04 install disk and tried to run it from there - it still failed (I did a disk check - OK). So I found a bios update (System Bios Update No 205 for American Megatrends v02.59 with VGA Bios VER009.012.001.027.A08409.002) and applied that. Now I cannot even boot into 6.10 - an x-server error. So I seem to be stuck. Any suggestions?

---

### Post by 1337PSPer on 2007-05-28
hmmm..... i get the same error on my ASUS G2P, I  wonder if its a ASUS thing :(

---

