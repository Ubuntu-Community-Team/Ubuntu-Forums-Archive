---
title: "Live CD does not detect HDD on old Dell"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by zeno23 on 2008-04-09
I'm trying to install Ubuntu 7.10 on an old Dell Dimension 4100. The BIOS (version A11) detects the hard drive, a 40 gig IDE Western Digital. When I boot with the Live CD, however, there is no hard drive detected. Everything else in hardware info looks OK. I have tried two different 7.10 discs and a 8.04 Beta CD. Same result: no HDD detected.

Just to be clear, this is a single-HDD system.

I recently zeroed the drive and reinstalled WinME with the OEM disc. WinME setup detected the drive, installed, the installation runs, etc.

Anyone help? :confused:

---

### Post by Pumalite on 2008-04-09
Memory?

---

### Post by zeno23 on 2008-04-09
256 Mb

---

### Post by Pumalite on 2008-04-09
With that RAM you cannot boot a Live CD. Try Xubuntu Alternate CD:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
It's your best bet.

---

### Post by a2xm on 2008-04-10
Hi,

I've almost the same problem here. I've a Pentium 4, 1gb RAM and 80gb HDD dual boot ubuntu 5.10 with win xp pro. everything works normally here for years.
A few months ago I changed the mainboard, Core2Duo 1.8ghz processor, and 1gb RAM but preserved the 5 years old 80gb HDD. I've reinstalled the win xp sucesfully. the GRUB menu also still there but I couldn't use the ubuntu 5.10 anymore, it said my /dev/hda5 doesn't exist. That's OK, because I want to updated with 7.10 anyway.

The problem appeared  when I want to install the ubuntu 7.10 using liveCD. It didn't detect the HDD. I've try using Kanotix liveCD as well with the same result. Until I added a new SATA2 HDD 160gb and successfully installed ubuntu 7.10 there, but ubuntu still couldn't see my old 80gb HDD with fdisk -l.

The BIOS can detect both HDDs. So, I've to change the boot sequence of HDD in the BIOS every time I want to use ubuntu (the new HDD).

Anyone can help? Thank you in advanced.

---

### Post by Pumalite on 2008-04-10
Post:
sudo fdisk -lu

---

### Post by thebigbluecan on 2008-04-11
I had a similar problem... I tried 2 western digital drives and both didn't show up in the partitioner or the installer on the live CD... I thought it was the mobo or ide cables... Replaced ide cables and still didn't work. One was a new (80gb) Western digital drive and one was from like 2002 (40gb)... Anyway I gave up for a couple of days.. came back tried again and still didn't show up... Went and grabbed an old samsung Hard drive from like 1999 and it showed up and worked with no problems. It could have been the drives were bad or a western digital thing. If you have any other drives laying around.. give it a try.  Good Luck :)

The 40gb drive  S/N that didn't work for me is WMAAT3040590

---

### Post by Pumalite on 2008-04-11
[http://ubuntuforums.org/showthread.php?t=690315](http://ubuntuforums.org/showthread.php?t=690315)

---

### Post by Pumalite on 2008-04-11
[http://ubuntuforums.org/archive/index.php/t-197642.html](http://ubuntuforums.org/archive/index.php/t-197642.html)

---

