---
title: "Computer won't boot ANY Linux Distro..."
date: 2011-11-22
forum: Installation &amp; Upgrades
---

### Post by solid.aqua on 2011-11-22
This problem is driving me crazy. My computer has never been able to even get past the first ubuntu splash screen when running from a live CD. I have tried with Ubuntu 8,9,10,11, server editions, x86 and amd64, Kubuntu 11, even Fedora(I know this might not belong here) all with no success. My computer just stops on the booting. In ubuntu, the four dots changing color go and go forever. In KDE, only the blue screen appears. Ubuntu server halts on a line saying (i believe) "running debian-installer". I have never ever been able to boot my system to a linux distro, let alone install it. The only exception to this is Parted Magic, which works like a charm, but can hardly be used as a desktop OS.  I have performed many successful installations on other computers.
What is the matter?? 
Below are my hardware specifications.

CPU:       AMD athlon 64 processor 3200+ 2.01GHz
Motherboard:   Chaintech VNF4-Ultra Edition
RAM:      1,5 GB 
GPU :      Nvidia Geforce 6600 256MB
Internal HDD Sata to IDE 500GB
always connected External USB Western Digital MyBook 500GB.
OS: Windows XP Home.
If you think something not mentioned is related, ask me and I'll find out.

Thanks

---

### Post by darkod on 2011-11-22
Did you try "playing" with the graphics card? Tried booting the cd in live mode with safe graphics, or with nomodeset on?

---

### Post by bluexrider on 2011-11-22
This may be nothing at all but I was having glitches until I turned off my external HDD before installing.

---

### Post by Quackers on 2011-11-22
Nomodeset looks like a good idea to me :-)

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by sudodus on 2011-11-22
Browse the internet for [http:///www.knoppix.net/]("http://www.knoppix.net/")
***Knoppix*** is known to be good at recognizing hardware. Learn about the Knoppix cheat-codes, that make it possible to manually tweak the boot procedure. Knoppix is not meant to be installed, but runs as a live session from a CD or USB drive. I would say that it gives you a full linux experience anyway, so after a while you can take the next step and install an Ubuntu system to your internal drive.

The tip about Nomodeset is equvalent to such a cheat-code.

---

### Post by solid.aqua on 2011-11-23
I will try the nomodeset and removing the external and let you know. Thank you:)

---

### Post by mastablasta on 2011-11-23
also when you see Ubuntu dots you should be able to hit ESC and see whhere the boto got stuck.
 
Some graphic card need parameters input before boot or need a safe mode boot (in winXP you would always boot into safe vga mode before you install the drivers). so in this case setting a parameter for that might help. also some cards can't boot via liveCD but work upon install through alternate cd. the alternate CD has a text based installer and you can install the drivers in the end i believe.

---

### Post by Mag107 on 2013-04-26
Hello, this won't help you but it may put your mind at rest as I too can't run ANY Linux Distro...either live or installed and USB...

---

### Post by oldos2er on 2013-04-26
Closed, please don't bump old threads.

---

