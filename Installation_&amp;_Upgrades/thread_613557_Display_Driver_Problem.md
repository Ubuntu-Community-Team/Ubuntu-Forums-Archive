---
title: "Display Driver Problem?"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by sathish456 on 2007-11-15
I have installed ubuntu 7.04 in my system. I have a Intel Desktop Board D102GGC, which has a Integrated "**ATI RADEON XPRESS 200**" graphics card. 

I am very new to linux & unable to load the display drivers. Please help to configure the display drivers. I want to use beryl application in my machine. 

Does any using D102GGC motherboard able to load display drivers.  

Regards,

---

### Post by erfahren on 2007-11-15
my video card is equivalent. To enable the propriety ATI driver (fglrx) go to System > Administration > Restricted Drivers Manager and check the driver then reboot.

to run Beryl (or Compiz Fusion) on Feisty you need to run it under XGL. I suggest Compiz Fusion, it was less problematic for me at least.

I used a combination of these HowTos (a couple cover Beryl as well I think):
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
[http://ubuntuforums.org/showthread.php?t=482773](http://ubuntuforums.org/showthread.php?t=482773)
... and created a script to delay Compiz-
Fusion's startup by a few seconds as given here: [http://ubuntuforums.org/showthread.php?t=501925](http://ubuntuforums.org/showthread.php?t=501925) 

Note: For Feisty - the current(?) repostitories that need to be added to /etc/apt/sources.list are 
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
(once you have Compiz-
Fusion installed you should comment the repositories back out by putting a # in front of them. There was a bug with them that would notify that there was an update when there actually 
wasn't one.)

good luck

---

