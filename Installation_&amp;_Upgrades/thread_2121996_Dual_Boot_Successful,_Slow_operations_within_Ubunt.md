---
title: "Dual Boot Successful, Slow operations within Ubuntu, Normal speeds in Windows 7"
date: 2013-03-03
forum: Installation &amp; Upgrades
---

### Post by dlanthoney89 on 2013-03-03
Greetings, getting into Linux in order to assess it's viability to replace my regular OS (windows) for a more PC oriented experience as opposed to a tablet style.  I have logged into Ubuntu successfully, updated the latest software, logged into google chrome, browsed, followed some valuable tips from this video [https://www.youtube.com/watch?v=S6M2GjvI8EQ](https://www.youtube.com/watch?v=S6M2GjvI8EQ) and have been poking around Ubuntu with eyes wide open.  

I'm starting this forum because it seems that Ubuntu is bottlenecking my processor down to 1 core of it's 4, I will leave spec's below in order to help trouble shoot the issues I may be having within Ubuntu.  When I run the system monitoring tool it shows my four cores (identifies and acknowledges that they are there)  but only shows one core at 100% the rest are at 0% of operation capacity.  I've downloaded the 64-bit Ubuntu as my dual boot thinking my computer could handle it just fine since I am running windows 7 64-bit home without any problems or operational bottle necking.  I was wondering if there is an app or some unknown AMD driver in order to unlock my cores and make Ubuntu fast enough to actually multitask like my windows does.  

Please any help would be greatly appreciated, once I speed up ubuntu I will be looking into WINE in order to play some windows games and assess their operation within Ubuntu for my next build which will be happening within the next few months.

Specs:
AMD Phenom 965 black edition - o.c. to 3500GHz per core
Nvidia GTX 570 2G ram gpu
Gskill 8G 1500
Seagate 1T HDD
ASUS M4A78T-E MOBO
Antec 850 gold-cert PSU

OS:
Windows 7 Home Premium 64bit
Ubuntu 12.10 64bit

---

### Post by fantab on 2013-03-03
How did you install Ubuntu? Through Wubi or normal install?
Have you used "**Try Ubuntu**" option from your Ubuntu LiveCD/USB to check if everything works before you installed. "Try Ubuntu" option gives you a working desktop without installing anything on your machine. It is an excellent way to see if all hardware on your machine works with Ubuntu install, especially graphics and online connectivity. 

Sometimes its possible that you have a bad install in spite of no warnings or error messages... so re-install can be an option.

---

### Post by bcbc on 2013-03-04
Use nomodest for your graphics card and then check additional-drivers for an update. See [http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it]("http://askubuntu.com/q/162075/14916")

---

### Post by dlanthoney89 on 2013-03-04
I downloaded it through the windows installer and selected the dual boot option.  It's not a simulated it's a full copy from my understanding from the installer, no flash drive or CD/DVD was used in its install.

---

### Post by ManamiVixen on 2013-03-04
Did you install your graphics drivers? Try installing nvidia-current-updates

---

### Post by Mark Phelps on 2013-03-04
Couple of comments ...

1) Multicore processor: I'm using a Phenom 1060 6-core and ALL of the cores are being utilized on Ubuntu 12.04 and 12.10 without problems. I know this because I have installed GkRellm on both and can actively monitor the utilization of individual cores.  Granted, I'm using 32-bit PAE versions, but this shows that recent Ubuntu versions can use multi-core processors.

2) Gaming -- if your plan is to play Windows games, you're in the wrong OS, Wine included.  You should do two things in this regard.  First, check in the Gaming section to see if others have experience trying to play the games you want but in Linux.  You may luck out and yours are among the FEW that actually play well with Wine.  Second, go to the Wine HQ website, the application compatibility database, and look up the games and versions you want to play.  IF you get Not Found, or ratings lower than Gold, attempting to install and use the games is going to be essentially a waste of your time.

---

