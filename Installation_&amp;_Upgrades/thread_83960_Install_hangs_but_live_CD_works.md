---
title: "Install hangs but live CD works?"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2005-10-30
I gave up trying to install Ubuntu onto my P2-350 with sis parts and yamaha sound on board but would like to know if the following eroors means there is no reasonable way of installing Ubuntu onto it. The 5.04 live cd sort of worked on it with problems but I tryed 5.04 and 5.10 and got the following errors during installation or the base system around 71%. The CD should be good as I used it to install on my main system. The thing that gets me is the Live CD worked.

[!!] Install the base system
No installable Kernal found in the defined APT sources

The current default Kernal package is 'kernal-image'.

You may try to continue though this rather strange error is probably fatal.

 I tryed to continue and it pooped out.

---

### Post by manicka on 2005-10-30
maybe try it with the acpi=off option

---

### Post by Omnios on 2005-11-01
Well I managed to disable the onboard sound which consisted of closing a jumper on the motherboard and got the soundblaster working in win 98. The only other thning I found in 98 was reference to sis usb in conflic/ shared which may be causing the problem. The only other thing I can think of is the Houston Tecknology 747 mother board and ami biosy might be incompatible with Linux though the Live cd worked with some monitor problems which is probly because the KTX monitor identifys itself as a LCD which it is not. 

 The acpi=off option didnt help any though it may be a bugged component such as the usb as I have it turned off int the biosy yet still showes up in 98. Im tempted to do a server install and try to install a desktop from there but am getting frustrated with spending hours to see if something works or nor. Anyways any suggestions would be apreciated. 

 Im tempted to turn off the IRQ 14 and 15 in biosy which seem to be usb components if I remember correctly.

---

### Post by Omnios on 2005-11-01
Think I found a magore problem. I was doing a server install and the text scrolls a little bit slower and it said something about but speed assuming it is 33mhz. My dustball has 100mhz bus speed so im assuming that its not getting the proper info from the biosy. It also assumed the cpu speed a long time ago but got that right. Im assuming it has no clue on what kernal to install or is trying to install one that no longer exsists on the cd, not shure though. As I said the live disk works and if it supports P2 then thats probably the one I want.

---

### Post by Omnios on 2005-11-01
Well just spent a couple hours doing a base server install and got a no suitable kernal error, the default kernal  lada lada la default kernal is kernal image. 

 Im assumming im waisting my time trying to install Ubuntu on this machine.

---

