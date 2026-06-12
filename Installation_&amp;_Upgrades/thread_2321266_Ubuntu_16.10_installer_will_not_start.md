---
title: "Ubuntu 16.10 installer will not start"
date: 2016-04-21
forum: Installation &amp; Upgrades
---

### Post by evan33 on 2016-04-21
Hardware: 
MSI X99A SLI PLUS (UEFI)
16GB Crucial Sport Ballistix RAM
EVGA GeForce GTX 960 Superclocked

Samsung 850 EVO 500GB SSD (Destination):
Windows 10
(I will do partitioning in the installer)

Crucial MX200 1TB SSD (Data drive)
UEFI DVD player (Unsure of brand)

Issue:
So, I have had an issue installing Ubuntu (16.04 LTS). So, when I boot from the install media, I get GRUB and have tried "Try Ubuntu without installing" and "Install Ubuntu". With both, I get a blank screen when I press enter. I have checked my UEFI firmware settings and everything seems to be OK. I even tried tinkering with settings that shouldn't matter. I also tried different installation media. I tried A. A 128GB USB 3.0 drive (formatted to 16GB for FAT32 compatibility) using Rufus, a 32GB USB 3.0 Drive using Rufus, and a DVD-RW DVD. The USB drives are Lexar, and the DVD is Memorex. I also tried booting from rEFInd and using built-in options.

---

### Post by anon24 on 2016-04-21
I don't think this is just your system. I have an MSI GS-70, I had Ubuntu 15.10 running perfectly. 

I did an auto upgrade, big mistake. Now, 16.04 installed, but it only gets to the log in screen. If I type in my password correctly, the screen goes black and then the log in screen just pops back up.

I'm not sure what to do, but I just wanted to let you know that you're not the only one having issues with the update.

---

### Post by EowynCarter on 2016-04-22
I have the same issue. login screen all over again. Graphic driver all messed up. Card is an nvidia as well ?

Recovery mode, and an "apt-get purge nvida*" forced the fallback to the nouveau drivers. Works better. But, you lose the features of the proprietary drivers.

---

