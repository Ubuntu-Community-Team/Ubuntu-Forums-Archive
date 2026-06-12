---
title: "Itronix ix250 Ubuntu 11.10"
date: 2012-04-09
forum: Installation &amp; Upgrades
---

### Post by theknightlinux on 2012-04-09
Hello. I have an Itronix Gobook ix250. It has a 800mhz cpu and I've upgraded it to 512mb of ram. I'd like to install Ubuntu 11.10 and get rid of the Windows 2000 installation it has. However, I'm struggling as it only has a floppy drive to boot from, and I got an external cd/dvd drive via USB. I'm planning on installing Ubuntu 11.10 and then adding E17 as the GUI. Can anybody help me on installing it. I have tried to boot with Plop, boot manager and even the puppy floppy image disk but with no sucess with any of them. I've been trying to boot with a floppy to the USB CD Drive. Any help or suggestions will be really appreciate it.

---

### Post by searchfgold6789 on 2012-04-09
See [https://help.ubuntu.com/community/Installation#Installation_without_a_CD](https://help.ubuntu.com/community/Installation#Installation_without_a_CD) to explore your options.

---

### Post by theknightlinux on 2012-04-09
Thank you Search. I have checked that page out, and have tried several of the options. However, none seem to work. The closer I was was when installing with plop, but the computer just stayed in black screen and it said something like plpa20! and it staid there for like 2 hrs, so I decided to just turn it off. I tried it with Ubuntu 11.10, and with the minimal install cd too. As of now I am thinking if a network install would be my best bet, but I don't find any detailed instructions for this. Thanks.

---

### Post by searchfgold6789 on 2012-04-10
So it sounds like you're having trouble booting from floppy. Ensure that it is first in the boot order in the BIOS settings.

---

### Post by theknightlinux on 2012-04-10
Search, I did change the settings as you suggested. Now, I'm trying to install PuppyLinux with the wakepup flopp. I was trying it before your suggestion and it couldn't boot up the CD, giving me a very large message. Now, that I changed floppy as the primary boot the message changed and it says: Can't Open Kernel File.

---

### Post by theknightlinux on 2012-04-23
OK. I'm just writing this for anyone that is looking to revive their old IX250 notebook, and can't find a way. Or if someone has similar questions like mine, and happened to come to this page, so that he/she has like a conclusion of what I did to finally revive the IX250. Well, I finally had to buy a DVD-ROM Drive, which I got for around $20. I inserted it, and the Live Ubuntu 11.10 CD didn't want to boot, neither a Puppy CD nor a Fedora, then I inserted the Ubuntu 11.10 Minimal Install which did boot. I installed Ubuntu with the Minimal CD, and the computer boot to the hard drive and all. However, I found it pretty slow and not with good performance even with a lightweight Desktop Environment which was E17. I then tried to install Ubuntu 11.10 with the normal CD, this time it did boot. I noticed that the computer had to be turned on for a while for the DVD-ROM to detect any media to boot from. I don't know what was with it, but it was nothing about the BIOS settings. Any way, after the install with Ubuntu 11.10, with a connection to the internet, I did notice a better performance on the IX250, and all drivers including the ones for the touchpad and the touchscreen were installed automatically (just as with the Minimal Install). For the desktop environment, I installed e17, and uninstalled any other desktop environments like Unity. I setup e17, and it did work quite well. However, there's a problem with the touchpad, as sometimes the mouse arrow freezes or gets stuck for awhile. The touchscreen was present, but it was not working, all I did was to install xinput-calibrator, run it and calibrated the screen. It worked like a charm, real nice. For the touchscreen to make it permanent I had to save a file to the xorg folder, and after a computer restart the touchscreen stays with the calibration. Other additional task I did was to uninstall Ubuntu Software Center, and other applications that took too much resources of the IX250 and installed lighter ones to do the task, for example instead of Ubuntu Software Center, I installed Synaptic. I also installed lightweight games, web browser, etc. All in all, the computer is working really nice with e17, and I can browse the web and do basic stuff with it. Well, not so basic, as I installed MyPaint and am doing real nice things with it with the touchscreen and a stylus. As I say, the only problem with it is the touchpad, and I haven't find a solution for it, but I am don't hesitate for that.

---

