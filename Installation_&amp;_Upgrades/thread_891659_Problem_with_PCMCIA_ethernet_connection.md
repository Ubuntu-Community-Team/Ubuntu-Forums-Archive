---
title: "Problem with PCMCIA ethernet connection"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by martinpg on 2008-08-16
Hi, my problem is this: I have a Toshiba laptop with an ethernet PCMCIA card. Because of problems with the CD drive, I performed an installation of Ubuntu onto the machine using the Install from Knoppix approach (see [https://help.ubuntu.com/community/Installation/FromKnoppix](https://help.ubuntu.com/community/Installation/FromKnoppix)). I have got to the point of being able to boot up, but I cannot get the ethernet connection to start up. During the boot process, I can see:
eth0: ERROR while getting interface flags: No such device

I know that the ethernet PCMCIA card works because I was able to install Ubuntu via the network when booted up into the Knoppix environment. I have tried to modprobe for 3c59x which works and have specified an alias eth0 3c59x so that modprobe eth0 also works.

I suspect that the problem is really that when the machine boots up, it either cannot find or cannot access the PCMCIA card. If I do lsmod when booted using the Knoppix CD, I can see listed (among others), the modules:
3c574_cs
pcmcia
pcmcia_core

However, if I boot up from the new Ubuntu installation, then running lsmod only gives a short list of modules and the three listed above are not in the list. If I modprobe for either either 3c574_cs or pcmcia then I get:
FATAL: module 3c574_cs not found
FATAL: module pcmcia not found

It looks like I can modprobe pcmcia_core, but this does not seem to fix the problem.

Can anyone describe to me the process I should take to diagnose and fix this? If it helps, here's what I get when I run uname -r: 2.6.8-4-386

Thanks for any help, Martin

---

### Post by martinpg on 2008-08-16
I should add that if I run lspci then I see the following list:

Host bridge
CardBus bridge
CardBus bridge
VGA compatible controller
USB controller

Thanks, Martin

---

### Post by martinpg on 2008-08-18
Just a reply to my own post in case anyone has the same problem. It turns out that the base install of Debian (which I installed using the Knoppix method) does not include support for PCMCIA.

I solved my problem by using the Knoppix live disk again to boot up, and then chrooting to the Debian installation. I then tried to apt-get install pcmciautils (not found), pcmcia-cs (could not install because of a ksyms error), and eventually kernel-pcmcia-modules - which did work.

I then rebooted into the Debian installation and this time the PCMCIA card was discovered. Thanks, Martin

---

### Post by caillean on 2008-08-18
Hey Martin,

just in case it's still interesting for you:

I had the same problem with Ubuntu and a pcmcia ethernet card once, and the reason was: Ubuntu did not install a package called pcmcia-cs by default. After installing this package, the card worked without problems.

Best regards,
Caillean

---

