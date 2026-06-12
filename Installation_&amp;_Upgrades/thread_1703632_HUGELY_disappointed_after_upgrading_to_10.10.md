---
title: "HUGELY disappointed after upgrading to 10.10"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by Old *ix Geek on 2011-03-09
Last night I decided to stop procrastinating and at least upgrade one of my computers--so I chose the one I use 99.99% of the time, my laptop. (Brilliant, I know.) My previously SUPER FAST laptop. I went from 9.10 to 10.10, doing a clean install of the OS. All I can say is, wow, am I UNDERwhelmed. It has brought my previously fast laptop to a crawl.

I've tried every variation of hardware drivers and disabling desktop effects, to no avail. It's slower than I can even describe. And its effects don't display correctly, like title bars on apps partially break up and show some of what's behind them. Awful. Just awful.

Before I wipe / and reinstall 9.10, I thought I'd give this a whirl and see if anyone has any ideas on what else I can do/try to improve its performance. The laptop is an HP dv6000, and I've tried all of the NVIDIA drivers that are available.

Oh, one good thing--my Broadcom 43xx wireless was no issue at all. Hasn't been for the last few releases, but I just thought I'd throw that out there. This is a 4-year-old laptop and I did NOTHING to get wireless working on it, other than activate the Broadcom STA driver. Done! :D

---

### Post by beew on 2011-03-09
Maybe it would help if you tell us your hardware. 10.10 is super fast on all computers I have tested on (4 of them all with different specs)

---

### Post by Old *ix Geek on 2011-03-09
> **beew said:**
> Maybe it would help if you tell us your hardware.Good thinking! :)
```
Processor: AMD Sempron 3200+ 1.6 GHz Data Bus Speed 1600.0 MHz

Cache Memory: Type L2 cache Cache size 512.0 KB

RAM: Installed Size 512.0 MB / 2.0 GB (max) Technology DDR II SDRAM

Storage controller type Serial ATA

300 GB hard drive

Display Type 15.4 in TFT active matrix Max Resolution 1280 x 800

Graphics Processor / Vendor NVidia GeForce Go 7200 Video Memory 256.0 MB

Audio output type Sound card Audio Input Microphone

Input device type Touchpad, Keyboard, Logitech trackball

Telecom: Modem Fax / modem Max Transfer Rate 56.0 Kbps Protocols & Specifications ITU V.90

Networking: Data link protocol Ethernet, Fast Ethernet, Gigabit Ethernet; Broadcom 43xx wireless

Expansion Slots Total (Free) 2.0 Memory , 1.0 ExpressCard 54/34 Interfaces 1.0 x Ethernet - USB 2.0 , 1.0 x S-Video - RJ-45 , 3.0 x Microphone - RJ-11 , 1.0 x Display / video - VGA , 1.0 x Expansion , 2.0 x IEEE 1394 (FireWire) , 1.0 x Headphones , 1.0 x Consumer IR , 1.0 x USB 2.0 , 1.0 x Modem

Battery: Technology Lithium ion Installed Qty 1.0
```

> 10.10 is super fast on all computers I have tested on (4 of them all with different specs)This has put a screeching halt on my plans to upgrade the rest of my computers. I'd rather stick with 9.10 than feel like I'm plodding through frozen molasses! :eek:

---

### Post by YesWeCan on 2011-03-09
How much swap space is it now using?
512MB of RAM is cutting it fine.

---

### Post by IcarusR on 2011-03-09
> RAM: Installed Size 512.0 MB / 2.0 GB (max) Technology DDR II SDRAM


512Mb ram is not much & I would suspect is your problem. Either install more ram or install xubuntu which requires less resources than full gnome version.

---

### Post by Old *ix Geek on 2011-03-09
> **IcarusR said:**
> 512Mb ram is not much & I would suspect is your problem. Either install more ram or install xubuntu which requires less resources than full gnome version.Thanks, but I don't use GNOME, I use KDE. :)

I think I've solved the problem. I had logged in as root and noticed that the system wasn't slow at all. So, light bulb goes off, and I created a new user and logged in with it. Same, nice and fast. Then I selectively copied over files from my original account, leaving behind all my highly-tweaked configuration files. Guess what? Speed! :D

So, apparently, my 'real' account has gotten so bogged down in my customization tweaks that it actually was affecting the performance I was seeing. I'm marking this thread solved as I now believe it is!

---

