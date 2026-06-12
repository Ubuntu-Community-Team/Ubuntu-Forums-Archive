---
title: "How to really test a system using live CD?"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by tomreid on 2010-03-20
Hi all, 

I'm thinking of transitioning my Dell Mini 10V netbook to 10.04, but I have a question about how to really test the hardware. 

When I run the system and chose to "try Ubuntu out without making any changes to my system", the first thing I notice is that the wifi does not work. 

This is fairly normal, as the "hardware drivers" menu tells me I need to download and activate a propitiatory broadcom driver to make the wifi work. But to complete the install of the broadcom driver the system tells me I need to re-boot. Surely if I reboot a system running in "live cd mode" I'll just lose the changes as my understanding is that each time I boot from a live cd it just loads the "vanilla" Ubuntu?

So how can I really test that this broadcom driver will install and function properly?

As an aside, the Alpha version of 10.04 seems to have a bug, when I try to download the broadcom driver, I get the error: [I]SystemError: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/gcc_4.4.2-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/gcc_4.4.2-3ubuntu1_i386.deb) 404  Not Found [IP: 91.189.88.40 80] 

[/I]I'm pretty sure this is a bug, as when I tried out 9.10 running as a live cd in the same machine, the process seemed to work fine, it's just I got stuck as I'm pretty sure if I re-boot, I'll just be back at the vanilla install agan.

cheers

---

### Post by gordintoronto on 2010-03-20
If you open a terminal and enter the command:
lspci
you will get a precise identification of your wifi card.  Even knowing you have a Mini 10V is not sufficient, because Dell is known to change components without changing the computer model code.

Google the precise identification (eg. BRCM4318) and the word "linux," and read the links which are current posts here, there and everywhere. You should be able to get a clear picture about whether the WIFI can work, and how painful it is to get it working.

It shouldn't be terribly difficult, because Dell sells 10Vs with Ubuntu installed, in some places.

Version 10.04 is being tested. You should expect it to fail. The current version is 9.10.

---

