---
title: "Installation of 7.10 hangs on HP Pavilion dv6140us notebook"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by ggtsu on 2008-04-19
I'm installing on:
HP Pavilion dv6140us Wide Screen w/Webcam
AMD Turion 64x2 TL-56
2 GB RAM
120 GB SATA Hard Drive
Nvidia GeForce Go 6150 Video
DVD/CD RW LightScribe drive
Broadcom 802.11B/G (94311) Network Adapter

After I choose to install / start live cd, I get to the progress meter with the ubuntu logo. It then switches to a console and starts initializing things. After it goes through a few items, I get to a black screen and the installation just hangs. There is no activity from the dvd or hd, and I eventually have to shut down my notebook. I noticed a two errors while the installation is trying to initialize things. Something about microcode and whatnot (the errors are hard to catch). I've tried to install both the 32 and 64 bit versions, with the exact same result on both. I'm close to giving up on ubuntu at this point so any help would be appreciated and enlightening...

---

### Post by Pumalite on 2008-04-19
There could be a number of problems. To inform yourself, here are a few links:
[https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu](https://wiki.ubuntu.com/hp_dv6000_series_(dv6116eu))
[http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/](http://www.linuxquestions.org/questions/ubuntu-63/hp-pavilion-dv6000-series-Wireless-driver-issues.-403326/)
[http://ubuntuforums.org/showthread.php?t=582220](http://ubuntuforums.org/showthread.php?t=582220)

---

### Post by ggtsu on 2008-04-19
Thanks for the links. I've finally managed to get this thing to start. I'm using "noapic nolapic" on startup. Am I losing any kind of crucial functionality with these command line options? I really want to commit to installing ubuntu, but I've read some less than encouraging reports about hardware support in ubuntu 7.10 for dv6000 laptops. Should I wait for the upcoming version or even try an older version?

---

### Post by Pumalite on 2008-04-19
Go with noapic nolapic. You'll be fine. Try Alternate 8.04 Beta if you want.

---

### Post by ggtsu on 2008-04-19
I decided to try 8.04, and I'm happy to say that it works great. It even detected my wireless card, no problem at all. I'm starting to feel a bit better about ubuntu now :)

---

### Post by Pumalite on 2008-04-19
Good for you!

---

