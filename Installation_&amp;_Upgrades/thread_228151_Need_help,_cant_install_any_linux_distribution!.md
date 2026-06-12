---
title: "Need help, cant install any linux distribution!"
date: 2006-08-02
forum: Installation &amp; Upgrades
---

### Post by Cynical on 2006-08-02
To start off I'm going to list my system specs and some distros I have tried.

Specs:

Intel Core 2 Duo E6300
Gigabyte GA-965P-DS3
1GB Corsair DDR2-675 XMS
Pioneer DVR-111D  (I've also tried my brothers Nec drive and and some offbrand drive produced by a company called HL Data Storage)
320GB Seagate SataII HD

Distros:

Ubuntu 6.06 desktop
Ubuntu 6.06 alternative
Suse 10.0 DVD
SimplyMepis 3.4.3


Now on to my problem. It was very difficult to pinpoint. On the ubuntu desktop cd I would get the "mounting root filesystem" that hangs, as some users here are familiar with. On SimplyMepis it would be "failed to load filesystem". The most clear response I received was from the text install on the alternative cd, which was "CDROM drive not detected, insert floppy with drivers?".


Now as I've said I've tried several drives already just to make sure the problem wasnt an unsupported drive. So I've come to the conclusion that its a problem with my motherboard. As some of you may know, intel recently decided to remove IDE support from its latest chipset, 965 Express. Not the wisest of moves but many manufacturers made up for it by adding their own IDE controllers. I'm fairly certain that the problem lies here. However, besides this problem my drive works just fine, so I'm really at a loss. Please help.

---

### Post by Cynical on 2006-08-05
nevermind, found a quick fix until edgy final is released.

---

### Post by philippe_carlo on 2006-08-05
Serail ATA controllers can be a pain. You need the drivers to be loaded before mounting the root file system, so they should be compiled into the kernel. Otherwise you get the symptoms you described. What exactly is your 'quick fix'?

---

### Post by Cynical on 2006-08-06
I decided to install over the internet.

---

