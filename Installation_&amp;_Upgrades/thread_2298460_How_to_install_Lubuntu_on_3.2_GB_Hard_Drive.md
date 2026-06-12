---
title: "How to install Lubuntu on 3.2 GB Hard Drive"
date: 2015-10-11
forum: Installation &amp; Upgrades
---

### Post by Mamsie on 2015-10-11
Hello I have a pretty old Computer with a 3.1 GB Hard Drive. (I have 1,5 GB RAM and CPU is also fast enough).

Currently there is Lubuntu 12 installed on the disk, I did that several years ago and it's all broken, so i want a fresh start.

I downloaded the .iso , booted from the CD (I am actually using it right now), but as soon as I want to start the installation, it says I need a minimum of 4.1 GB available space to install it. So I can't click on continue.

Can I somehow override that message or did Lubuntu double it's size from 12 - 15?
Sadly I don't remember how I installed Lubuntu 12 since the PC stood in a dusty corner for 3 years.


I don't know much about Linux yet, I am a stupid Windows user normally.

I hope somebody knows a solution, thanks already!


Greetings,
Mamsie :)

---

### Post by howefield on 2015-10-11
Using the alternate cd might be an option..

[http://cdimages.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimages.ubuntu.com/lubuntu/releases/14.04/release/)
[http://cdimages.ubuntu.com/lubuntu/releases/15.04/release/](http://cdimages.ubuntu.com/lubuntu/releases/15.04/release/)

Or even the minimal cd, but that may well be a bridge to far for you.

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by Mamsie on 2015-10-11
Thank you for answering so fast!

I thought about that and I wondered what would I be missing out on? Furthermore I already wasted so many CDs accedently that I wanted to ask if there is another option, because somehow it worked before.

But if you say so, I will try it with that .iso


Greetings,
Mamsie

---

### Post by v3.xx on 2015-10-11
Please run this command and post your computer specs.  Thankyou

```
sudo apt-get install inxi && inxi -b
```

---

### Post by Mamsie on 2015-10-11
```
System:    Host: lubuntu Kernel: 3.19.0-15-generic i686 (32 bit)
           Desktop: LXDE (Openbox 3.5.2) Distro: Ubuntu 15.04 vivid
Machine:   Mobo: N/A model: i845G-SMC192 v: 9132z10011
           Bios: Phoenix v: 6.00 PG date: 07/28/2003
CPU:       Single core Intel Celeron (-UP-) speed: 2400 MHz (max)
Graphics:  Card: NVIDIA NV17 [GeForce4 MX 440]
           Display Server: X.Org 1.17.1 drivers: nouveau (unloaded: fbdev,vesa)
           Resolution: 1024x768@75.1hz, 1024x768@50.0hz
           GLX Renderer: Mesa DRI nv17 x86/MMX/SSE2
           GLX Version: 1.2 Mesa 10.5.2
Network:   Card: Intel 82801DB PRO/100 VE (CNR) Ethernet Controller
           driver: e100
Drives:    HDD Total Size: 3.2GB (Used Error!)
Info:      Processes: 116 Uptime: 1:21 Memory: 437.9/1508.0MB
           Client: Shell (bash) inxi: 2.2.16
```

---

### Post by v3.xx on 2015-10-11
LXDE

That's as lite as it gets IMO

As suggested, the mini iso may get you by.

---

### Post by Mamsie on 2015-10-11
The Alternate ISO worked, but only at the second try where I deleted the SWAP partition.

I now have the full Lubuntu and still about 700 mb of free space!

Thank you!

---

