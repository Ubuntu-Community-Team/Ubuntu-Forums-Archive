---
title: "Installing libraries off line"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by leighharrison on 2008-09-06
Kia ora.

I've just successfully installed Ubuntu 8.04 as a dual boot with XP Pro. My only means of internet connectivity is my Belkin wireless adaptor (Broadcomm chipset) which doesn't immediately work. 

I've identified that I can install ndiswrapper and my XP drivers. I downloaded those at work, saved them to a CD, copied them to my Ubuntu Downloads folder and followed the install instructions. It was then I found Hardy doesn't pack the required c header files to build the packages. 

I've copied libc6 (and a disc's worth of other core files) onto another CD. However, I have no idea where to put them or what I need to do to them so I can build my wireless card driver and get on-line. 

Once I'm on-line, I think I'll be OK - I can use the standard mechanisms Ubuntu provides for managing installs. But I have to get on-line first. There is no way I can get the PC within cable distance of a router. 

I've figured I have three options, but I may have it wrong.

[1] get the necessary c header files into the right 
      location, build and install ndiswrapper, or

[2] find a pre-compiled driver to get me started (I have
      an Athlon 2400 and there must be someone ...), or

[3] give up and revert to XP. 

I really don't like option [3]. 

Can anyone tell me where to put, what to do with, libc6_2.7-10ubuntu3_i386.deb?

---

### Post by Wobblybob on 2008-09-06
I'm no expert but you have a .deb file which can be placed in any of your Ubuntu folders. You then double click on it and ubuntu should open it in the default package installer, just choose install and Bob's your Uncle.

Good luck

---

### Post by leighharrison on 2008-09-06
Thank you wobblybob. That was so easy (once you know)!

But it seems the distribution files I understood contained the missing c headers are already installed. This is strange, because the same research said they're not part of the Ubuntu distro. They don't appear in the manifest for the files I've harvested, anyway. Sigh.

Back to square one. Although I'm not sure now what square one is.

---

### Post by leighharrison on 2008-09-06
OK. Got the right packages this time. ndiswrapper set up and installed and apparently fine ... but still I can't see the world through my wireless adaptor. Sadly I can't put any more time into this now (and I'm quite disheartened). If I can face it, I might come back to this in a day or two.

In the meantime it's back to XP. Shame.

---

### Post by leighharrison on 2008-09-06
Incidentally, if anyone has any thoughts, I now see the following entry in the list for ifconfig -a ... 

wlan0     Link encap:Ethernet  HWaddr 00:30:bd:f6:57:1b  
          inet addr:10.1.1.13  Bcast:10.255.255.255  Mask:255.0.0.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Yes, I've tried roaming, and DHCP as well as the above Static IP settings ...

---

