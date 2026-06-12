---
title: "Lubuntu faster than Windows XP on old computer?"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by Seb71 on 2011-11-12
I tested Lubuntu 11.10 on an old computer which barely runs Winsows XP.

-----------
Configuration:
- MB Soltek 65kv2, VIA VT82C 694X Appolo Pro 133A Northbridge / VIA VT82C 686B Southbridge
- Socket 370
- Celeron 900MHz
- 256 MB SDRAM
- AGP 2x ATI Rage XL graphic card

It is above the minimum System Requirements listed for Lubuntu. 

Windows XP SP3 is installed on a slow 20GB IDE Hard Disk drive.

I installed Lubuntu on a (maybe even slower) 10GB IDE Hard Disk Drive.
-----------

The results were less than impressing. The PC is similarly slower with Lubuntu as it is with Windows XP. Memory usage is low enough, but the CPU is often overloaded (for instance when using Chromium browser, CPU usage is 100% or close to 100%).

Is this a typical conclusion?

Did you get better results with Lubuntu on similar configurations?

---

### Post by BillyBoa on 2011-11-12
Yes.

Windows XP is a very old OS from the year 2001.

Lubuntu 11.10 is designed to compete with the latest OSs and it's designed in the year 2011.

You cannot compare them.


It's better to try other Linux distributions which are far lighter and simpler to have a chance to get faster an old PC.

---

### Post by mörgæs on 2011-11-12
A 900 MHz Celeron is from around 2001, so don't expect too much regardless of operative system. Lubuntu should be quite a lot faster than Windows, though.

Surfing the web is a heavy task due to lots unneded Flash ads and the like. If the browsers are using so much CPU, but other applications run well, you could try adding Flashblock or similar plug-ins.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-12
Xubuntu runs faster than Lubuntu on my old comp...  it has a really nice interface, also...
Dooble is the fastest web browser I have found... though there is no bookmarking feature (that I have found...)  flash is disabled by default.... though you can turn it on to use sites that require it.

---

### Post by Matti L on 2011-11-12
Might want to try out [Puppy Linux]("http://www.puppylinux.com/").

---

### Post by snowpine on 2011-11-12
Simple, really... your computer does not meet the [minimum hardware requirements for Adobe Flash]("http://www.adobe.com/products/flashplayer/tech-specs.html"):

> Linux

    * 2.33GHz or faster x86-compatible processor, or Intel Atom 1.6GHz or faster processor for netbooks
    * Red Hat® Enterprise Linux (RHEL) 5.6 or later (32-bit and 64-bit), openSUSE® 11.3 or later (32-bit and 64-bit), Ubuntu 10.04 or later (32-bit and 64-bit)
    * Mozilla Firefox 4.0 or Google Chrome
    * 512MB of RAM; 128MB of graphics memory

If you block all Flash then you should be able to browse simple websites (such as Ubuntuforums) with the speed one would expect from ten-year-old hardware.

A better alternative (in my opinion) is to hit up Freecycle, Craigslist, Goodwill, friends, relatives, coworkers, etc. and upgrade your hardware. You'd be amazed what's available free or very inexpensively these days.

---

### Post by Jack Brown on 2011-11-12
browsers (and the sites we visit) need so much memory these days.

you can also try out a text-mode www browser like 'lynx'.
available in repositories.

windows XP with up to date updates plus antivirus would be so slow on 256mb ram (it's very slow on 512mb, even with a faster processor)

LXDE would still be more responsive.

(the memory in your setup is the first bottleneck, if you can find _super cheap_ (or free) old memory, it's the first worthwhile upgrade on that setup)

a 900 mhz netbook could actually still run ubuntu lucid 10.04 regular, and be able to surf the net.  still responsive.  this netbook has 512mb memory and a small SSD though.

---

### Post by Seb71 on 2011-11-12
I looked into Puppy Linux (and Damn Small Linux), but those seems a little to basic for my taste. Maybe I will give them a try.

I do not absolutely need to use that old computer, but if I can have another PC capable of simple tasks (browsing, word processor with native .odt files, picture viewer), why not?

> **TREESofRIGHTEOUSNESS said:**
> Xubuntu runs faster than Lubuntu on my old comp...  

I did not try Xubuntu on that PC because Lubuntu is supposed to be the lightest OS from Ubuntu family.

What is the configuration of that old computer?

---

### Post by mörgæs on 2011-11-12
Damn Small Linux is unsupported and hence a security threat. Don't install this one, though it might run.

---

### Post by TREESofRIGHTEOUSNESS on 2011-11-12
It is a Compaq presario R3000
output of lspci
```
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

```

It does have a graphics card, though it worked fine w/o it.
I tried Lubuntu, but it ran kinda slow.  I run puppy occasionally... and it is simple, but you can config it how you like.  You can run a different window manager like lxde, or xfce4...  you can also mix and match of course...  and a really light panel to use for a dock is tint2... but you have to manually config it.  JWM (what usually comes with puppy) is pretty nice, and puppy has a GUI tool to config it, though you can also manually edit the config.
I enjoy puppy quite a bit... it is my fav other linux distro for old comps or ones totally screwed up by windows (well... the viruses, really)... and I have tried quite a few.  PeppermintOS is pretty light also, but after using it, I just decided to go with Xubuntu because I have been a fan of Ubuntu since 7, and started using it often when Intrepid Ibex came out.  After that, I used win for a while, but around Maverick I switched completely.
I've always liked Debian, and I have been a fan of gnome... but I was really surprised with xfce... it is a lot like gnome classic (or now gnome shell).
Xubuntu has a lot of nice GUI tools implemented.  Give it a try.  Dual boot it for a bit and see what you think.

---

### Post by Seb71 on 2011-11-12
Your Compaq Presario R3000 is significantly more powerful than my old PC. That explains why you can run Xubuntu on it.

-----

So would it be correct to say that for Lubuntu you need at least a Pentium 4 or Athlon 64 based computer?

Minimum requirements for Lubuntu mentioning Pentium II are misleading (probably the OS would load on such a computer, but it would not be a usable desktop PC).

---

### Post by BertN45 on 2011-11-12
I did run Ubuntu 10.04 on a PII 400mHz and 384MB of memory, it was too slow for video, but everything else worked fine and so would Lubuntu. On my PIII 500mHz  with Lubuntu video works just about OK. The problem is not the OS or Desktop but the applications you want to run.

---

### Post by DustofDust on 2011-11-12
i think lubuntu is ok for ur hardware... the problems are the fat browsers like firefox and chrom/ium and even on quicker hardware they use 100% cpu...

try midori [http://www.twotoasts.de/index.php?/pages/midori_summary.html](http://www.twotoasts.de/index.php?/pages/midori_summary.html)

if its not in the main repo than add the repo of [http://www.getdeb.net/](http://www.getdeb.net/) (at the moment it is down)

even on old hardware it works nice :)

---

### Post by kurt18947 on 2011-11-12
> **DustofDust said:**
> i think lubuntu is ok for ur hardware... the problems are the fat browsers like firefox and chrom/ium and even on quicker hardware they use 100% cpu...

try midori [http://www.twotoasts.de/index.php?/pages/midori_summary.html](http://www.twotoasts.de/index.php?/pages/midori_summary.html)

if its not in the main repo than add the repo of [http://www.getdeb.net/](http://www.getdeb.net/) (at the moment it is down)

even on old hardware it works nice :)

  I tried Midori on Lubuntu and there were some rough spots. Opera works quite well though being more mature and seems about the same 'weight'.

---

### Post by marinara on 2011-11-12
lubuntu is less RAM intensive than xubuntu

---

### Post by kurt18947 on 2011-11-12
> **marinara said:**
> lubuntu is less RAM intensive than xubuntu

 True. Lubuntu+Firefox with this page loaded uses 183 MB. of 488MB available. Lubuntu+ Opera same page uses 128 MB. of 488 MB. available. These numbers are from Task Manager which would use some RAM itself.

---

### Post by mörgæs on 2011-11-12
The best measure for RAM usage is here:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

Sorry for the ugly page. The contents is fine, though.

---

### Post by Seb71 on 2011-11-12
RAM usage was not a problem on my old PC - for browsing it was used around 100MB (from 256MB total RAM).

---

### Post by dajare on 2011-11-13
I had a machine (Tosh Satellite A100; 256Mb RAM + Intel Celeron "M", 1.40Ghz) with Windows XP/SP2 on it that my son was using for university. He got so fed up with it (10+ mins to boot to usable state), that we got him a new machine and I took this one back.

I put Ubuntu 9.04 on it, and used it that way for about 1 1/2 years. Booted in about 3 mins. I could word-process, browse just fine. Opening multiple apps made it quite sluggish (surprise!), but it was acceptable. A while ago I bought 1Gb of memory for it for £10, and it was transformed.

I'm now running Lubuntu 11.10 on it. It boots in less than 50 seconds. Video seems slower, and I'm still tweaking and learning, but basically it's great.

---

### Post by vandamme on 2011-11-15
I also recommend Puppy. I use it on an old laptop (256M, 8 year old). You can't put a rocket engine in a Pinto.

---

### Post by claracc on 2011-11-17
I have lubuntu 11.04 running in an old pentium III, 1GHz laptop with 512 Mb Ram, from which 64 MB are used by sis 630/730 graphics card, 20 GB HDD.

This laptop had windows xp sp3 installed and it was a turtle, the pc worked only for the avast antivirus, I couldn't use it.

With lubuntu, this laptop is usable again and it works very well, taking into account the hardware is about 10 years old. I use it for surfing web basically.

It is true, chromium is too heavy to surf the web with it (100 % CPU usage and slow), I changed it by epiphnay-browser and results are far better (quick surfing and less cpu usage), of course I have installed the epiphany extensions to block ads and use greasymonkey scripts.

About playing flash videos, if I use adobe flash plugin to see videos in newspaper pages ( bbc news, the new york times) or in youtube, the video is in some intensive flash pages in slow motion and CPU is 100% usage; but for videos in youtube I use viewtube script from userscripts.org, which doesn't use adobe flash, and play the videos very well with about 50-60 % CPU usage.

For other flash videos websites I have to find the proper script (each flash video page uses its own container?) to play without adobe flash or doing it myself, but I am not a developer and I don't know how.

I have installed VLC and gnome-mplayer which work perfect with videos formats other than flash.

In conclusion I recommend to stay with lubuntu ( I haven't tried 11.10 yet because 11.04 is doing so well that why change?), change your browser for a lighter one, use an ads blocker and userscripts compatible and you'll get your old pc to new life again.

---

